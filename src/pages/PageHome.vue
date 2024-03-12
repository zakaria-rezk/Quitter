<template>
  <q-page>
  <div class="q-ma-md ">
    <q-input class="input" bottom-slots v-model="newTweet" label="What is in your mind right now!!" counter maxlength="280" :dense="dense" autogrow>
        <template v-slot:before>
          <q-avatar >
            <img src="https://cdn.quasar.dev/img/avatar5.jpg">
          </q-avatar>
        </template>

        <template v-slot:append>
        
          <q-icon name="schedule" />
        </template>

        

        <template v-slot:after >
          <q-btn push color="primary" text-color="white" label="tweet" size="md" rounded :disable="!newTweet" bottom/>
        </template>
       
      </q-input>
  </div>
  <q-separator size="10px" color="grey-2"/>
  <q-list bordered >
      
      <q-item  class="qweet q-py-md">
        <q-item-section avatar top>
          <q-avatar size="xl">
            <img src="https://cdn.quasar.dev/img/avatar2.jpg">
          </q-avatar>
        </q-item-section>

        <q-item-section>
        
          <q-item-label ><strong> Brunch this weekend?</strong>
            <span class="text-grey-7">
                  @danny__connell 
                
                </span> </q-item-label>
          
          <q-item-label class="whitespace" >
           
          
            -- I'll be in your neighborhood doing errands this
            weekend. Do you want to grab brunch?
          </q-item-label>
        </q-item-section>

        <q-item-section side top>
          1 min ago
        </q-item-section>
        <div class="qweet-icons row justify-between q-mt-sm">
                <q-btn
                  color="grey"
                  icon="far fa-comment"
                  size="sm"
                  flat
                  round
                />
                <q-btn
                  color="grey"
                  icon="fas fa-retweet"
                  size="sm"
                  flat
                  round
                />
                <q-btn
                 
                  
                  
                  size="sm"
                  flat
                  round
                />
                <q-btn
                 
                  color="grey"
                  icon="fas fa-trash"
                  size="sm"
                  flat
                  round
                />
              </div>
      </q-item>

      <q-separator inset="item" />

     
    </q-list>
  </q-page>
</template>

<script setup>
import { defineComponent, ref } from 'vue'

const newTweet =ref('')
</script>
<style scoped>
.input{
  font-size: 19px;
}
.whitespace{
  white-space: pre-line;
}

</style>
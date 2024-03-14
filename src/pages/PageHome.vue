<template :key="key">
  <q-page>
    <div class="q-my-md row items-end">
      <div class="col q-px-sm">
        <q-input
          class="input"
          bottom-slots
          v-model="newTweet.tweet"
          label="What is in your mind right now!!"
          counter
          maxlength="280"
          
          autogrow
        >
          <template v-slot:before>
            <q-avatar>
              <img src="https://cdn.quasar.dev/img/avatar5.jpg" />
            </q-avatar>
          </template>
        </q-input>
      </div>
      <div class="col col-shrink">
        <q-btn
          push
          color="primary"
          class="q-my-md"
          text-color="white"
          label="tweet"
          size="md"
          rounded
          :disable="!newTweet.tweet"
          bottom
          @click="addtweet"
        />
      </div>
    </div>
    <q-separator size="10px" color="grey-2" />
    <q-list  separator>
      <q-item class="qweet q-py-sm" v-for="tweet in tweets" :key="tweet.time">
        <div class="qweet-item">
          <q-item-section avatar top>
            <q-avatar size="xl">
              <img src="https://cdn.quasar.dev/img/avatar2.jpg" />
            </q-avatar>
          </q-item-section>

          <q-item-section>
            <q-item-label
              ><strong> Brunch this weekend?</strong>
              <span class="text-grey-7"> @{{ tweet.email }} . {{ tweet.time }} minute ago</span>
            </q-item-label>

            <q-item-label class="whitespace">
              {{ tweet.content }}
            </q-item-label>
          </q-item-section>

          
        </div>
        <br />
        <div class="qweet-icons row justify-between">
          <q-btn color="grey" icon="far fa-comment" size="sm" flat round />
          <q-btn color="grey" icon="fas fa-retweet" size="sm" flat round />
          <q-btn color="grey" icon="fa-regular fa-heart" size="sm" flat round  :class="{ 'liked': tweet.isliked }" @click="like(tweet)"/>
          <q-btn color="grey" icon="fas fa-trash" size="sm" flat round  @click="deletetweet(tweet)"/>
        </div>
      </q-item>
      <q-separator size="10px" color="grey-2" />

      <q-separator inset="item" />
    </q-list>
  </q-page>
</template>

<script setup>
import { reactive,ref } from "vue";
const key =ref(0)  

const newTweet = reactive({
  tweet:'',
}
);
const tweets =ref( [
  {
    content:
    'Lorem Lorem ipsum is placeholder text commonly used in the graphic, print, and publishing industries for previewing layouts and visual mockup',
    name: 'zakariarezk',
    email: 'zakariarezk0@gmail.com',
    time: new Date().getMinutes(),
    isliked:false
  },
  
]);
//add tweet
const addtweet = () => {
  const tweet = {
    content: newTweet.tweet,
    name:"zakariarezk",
    email: "zakariarezk0@gmail.com",
    time: new Date().getMinutes(),
  };
  tweets.value.push(tweet);
  newTweet.tweet=''
  
};
//delete tweet 
const deletetweet=(tweet)=>{
  const index =tweets.value.findIndex(t => t.time === tweet.time);
   tweets.value.splice(index,1)   
}
//liekd
const like =(tweet) =>{
 tweet.isliked =!tweet.isliked;
}
</script>
<style scoped>
.input {
  font-size: 19px;
}
.whitespace {
  white-space: pre-line;
}
.qweet {
  display: flex;
  flex-direction: column;
}
.qweet-item {
  display: flex;
}

.qweet-icons {
  margin-left: 62px;
  margin-right: 62px;
  /* display: flex;
  justify-content: space-around;
  align-items: center; */
}
.liked{
  background-color: red;
}
</style>
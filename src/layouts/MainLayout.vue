<template>
  <q-layout view="lHr lpR fFf">
    <q-header elevated class="bg-white text-dark">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title class="text-weight-bold">
          <span class="gt-sm">Twitter</span> 
          <q-icon name="fa-brands fa-x-twitter" size="lg" color="primary" class="q-pa-md lt-md absolute-center" ></q-icon>
           </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered :width="283">
      <!-- drawer content -->
      <q-icon name="fa-brands fa-x-twitter" size="lg" color="primary" class="q-pa-md"></q-icon>
      <q-list bordered>
      <q-item clickable v-ripple to="/">
        <q-item-section avatar>
          <q-icon name="fa-solid fa-house" />
        </q-item-section>

        <q-item-section class="text-h6 text-weight-bold" >Home</q-item-section>
      </q-item> 
      <q-item clickable v-ripple to="/about">
        <q-item-section avatar>
          <q-icon  name="fa-solid fa-circle-info" />
        </q-item-section>

        <q-item-section class="text-h6 text-weight-bold">about</q-item-section>
      </q-item>

      
    </q-list>
    </q-drawer>
<!-- drawer content -->
    <q-drawer show-if-above v-model="rightDrawerOpen" side="right" bordered>
      <q-input color="primary"  v-model="text" label="Search" class="q-ma-md" outlined rounded  dense >
        <template v-slot:prepend>
          <q-icon name="event" />
        </template>
      </q-input>
      <q-list padding separator>
      <q-item class="q-pa-sm">
        <q-item-section>
          <q-item-label class="text-grey">Eduction</q-item-label>
          <q-item-label class="text-weight-bold">Some Thing amazing happened!</q-item-label>
          <q-item-label caption>Secondary line text. Lorem ipsum dolor sit amet, consectetur adipiscit elit.</q-item-label>
        </q-item-section>

        <q-item-section side top>
          <q-item-label caption>5 min ago</q-item-label>
        </q-item-section>
      </q-item>
      <q-item class="q-pa-md">
        <q-item-section>
          <q-item-label class="text-grey">Eduction</q-item-label>
          <q-item-label class="text-weight-bold">Some Thing amazing happened!</q-item-label>
          <q-item-label caption>Secondary line text. Lorem ipsum dolor sit amet, consectetur adipiscit elit.</q-item-label>
        </q-item-section>

        <q-item-section side top>
          <q-item-label caption>5 min ago</q-item-label>
        </q-item-section>
      </q-item>
      <q-item class="q-pa-sm">
        <q-item-section>
          <q-item-label class="text-grey">Eduction</q-item-label>
          <q-item-label class="text-weight-bold">Some Thing amazing happened!</q-item-label>
          <q-item-label caption>Secondary line text. Lorem ipsum dolor sit amet, consectetur adipiscit elit.</q-item-label>
        </q-item-section>

        <q-item-section side top>
          <q-item-label caption>5 min ago</q-item-label>
        </q-item-section>
      </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const leftDrawerOpen = ref(false);
    const rightDrawerOpen = ref(false);

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },

      rightDrawerOpen,
      toggleRightDrawer() {
        rightDrawerOpen.value = !rightDrawerOpen.value;
      },
    };
  },
};
</script>
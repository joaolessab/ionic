<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Horizontal Scrolling</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-refresher slot="fixed" @ionRefresh="refresh($event)">
        <ion-refresher-content></ion-refresher-content>
      </ion-refresher>
      
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Horizontal Scrolling</ion-title>
        </ion-toolbar>
      </ion-header>
      
      <ion-list class="scrolling-wrapper">
        <HorizontalScroll v-for="message in messages" :key="message.id" :message="message" />
      </ion-list>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonList, IonPage, IonRefresher, IonRefresherContent, IonTitle, IonToolbar } from '@ionic/vue';
import HorizontalScroll from '@/components/HorizontalScroll.vue';
import { defineComponent } from 'vue';
import { getMessages } from '@/data/messages';

export default defineComponent({
  name: 'HomePage',
  data() {
    return {
      messages: getMessages()
    }
  },
  methods: {
    refresh: (ev: CustomEvent) => {
      setTimeout(() => {
        ev.detail.complete();
      }, 3000);
    }
  },
  components: {
    IonContent,
    IonHeader,
    IonList,
    IonPage,
    IonRefresher,
    IonRefresherContent,
    IonTitle,
    IonToolbar,
    HorizontalScroll
  },
});
</script>
<style scoped>
  .scrolling-wrapper {
    overflow-x: scroll;
    overflow-y: hidden;
    white-space: nowrap;  
  }
  .card {
    display: inline-block;
  }
</style>
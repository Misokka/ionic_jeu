<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 1</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 1</ion-title>
        </ion-toolbar>
      </ion-header>

      <h1>Bonjour à tous !</h1>

      <ion-item>
        <ion-label position="floating">Nombre</ion-label>
        <ion-input type="number" v-model="number"></ion-input>
      </ion-item>
      <ExploreContainer name="Tab 1 page" :number="number"/>

      <ion-button color="danger" @click="decrement()">Decrement</ion-button>
      <span :style="{color: number < 10 ? 'red' : 'blue'}">{{ number }}</span>
      <ion-button color="primary" @click="increment()">Increment</ion-button>

      <p v-if="number < 10">Je suis en dessous de 10</p>
      <p v-else>Je suis au dessus de 10</p>
    </ion-content>
  </ion-page>
</template>

<script>
import {defineComponent, ref} from 'vue';
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonInput, IonItem, IonLabel, IonButton } from '@ionic/vue';
import ExploreContainer from '@/components/ExploreContainer.vue';

export default  defineComponent({
  name: 'Tab1Page',
  components: { ExploreContainer, IonHeader, IonToolbar, IonTitle, IonContent, IonPage, IonInput, IonItem, IonLabel, IonButton },
  setup() {
    let number = ref(0)

    const decrement = () => {
      number.value--
    }

    const increment = () => {
      number.value++
    }

    return {number, decrement, increment}
  }
});
</script>

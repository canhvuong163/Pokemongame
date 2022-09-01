

<template>
  <MainScreen v-if="statusMath === 'default'" @onStart="onHandleBeforeStart($event)" />
  <InteracScreen v-if="statusMath === 'match'" :cardsContext="settings.cardsContext" @onFinish="onGetResult" />
  <ResultScreen v-if="statusMath === 'result'" :timer="timer" @onStartAgain = "statusMath = 'default'" />
 
</template>
<script>
import MainScreen from './components/MainScreen.vue';
import InteracScreen from './components/InteracScreen.vue';
import ResultScreen from './components/ResultScreen.vue';

import {shuffled} from './untils/array';
  export default {
    name: "App",
    components: {
      MainScreen,
      InteracScreen,
      ResultScreen,
    },
    data() {
      
      return {
        settings: {
          totalOfBlocks: 0,
          cardsContext: [],
          startedAt: null,

        },
        statusMath: "default",
        timer: 0,
      };
    },
    
    methods: {
      onGetResult() {
        //get timer
        this.timer = new Date().getTime() - this.settings.startedAt;


        //ket qua len man hinh
        this.statusMath = "result";
      },
      onHandleBeforeStart(config) {
        
        this.settings.totalOfBlocks = config.totalOfBlocks;
        // tao mang
        const firstCards = Array.from(
          {length: this.settings.totalOfBlocks /2 }, (_, i) => i + 1
        );
       
        const secondCards = [...firstCards];
        const cards = [...firstCards, ...secondCards];
        this.settings.cardsContext = shuffled(shuffled(shuffled(shuffled(cards))));
        this.settings.startedAt = new Date().getTime();
        this.statusMath = "match";
      },
    },
  };
</script>



<template>
  <div id="app">
    <div class="navigation_arrows">
      <button class="next" v-on:click="indexUp"><font-awesome-icon icon="chevron-down" /></button>
      <button class="prev" v-on:click="indexDown"><font-awesome-icon icon="chevron-up" /></button>
      <p>{{indexNumber}}</p>
    </div>
    <home id="home"></home>
    <front-end id="front-end"></front-end>
    <back-end id="back-end"></back-end>
    <databases id="databases"></databases>
    <editor :code="codeText"></editor>
  </div>
</template>

<script>
// Imports
import Vue from 'vue'
import Home from './components/Home.vue';
import FrontEnd from './components/FrontEndDevelopment.vue';
import BackEnd from './components/BackEndDevelopment.vue';
import Databases from './components/Databases.vue';
import editor from './components/Editor.vue';

// FontAwesome import
import { library } from '@fortawesome/fontawesome-svg-core'
import { faChevronUp } from '@fortawesome/free-solid-svg-icons'
import { faChevronDown } from '@fortawesome/free-solid-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

library.add(faChevronUp);
library.add(faChevronDown);
Vue.component('font-awesome-icon', FontAwesomeIcon);
Vue.config.productionTip = false;

export default {
  name: 'app',
  data: function (){
    return {
      codeText: '',
      indexNumber: 0,
      maxIndex: 5,
    }
  },
  components: {
    Home,
    FrontEnd,
    BackEnd,
    Databases,
    editor
  },
  methods: {
    indexUp: function () {
      if (this.indexNumber < this.maxIndex){
        this.indexNumber += 1;
      }else{
        this.indexNumber = this.maxIndex;
      }
    },
    indexDown: function () {
      if (this.indexNumber > 0){
        this.indexNumber -= 1;
      }else{
        this.indexNumber = 0;
      }
    }
  },
  watch: {
    indexNumber: function (newIndex) {
      switch (newIndex){
        case 0:
          document.getElementById('home').scrollIntoView();
          this.codeText = 'root@portfolio: <span class="command">npm run portfolio</span> <br> Starting portfolio... <br> Starting: Database <br> Starting: Server <br> Compiling... <br> Ready!'
          break;
        case 1:
          document.getElementById('front-end').scrollIntoView();
          this.codeText = 'root@portfolio: npm run front-end <br> Starting portfolio... <br> Starting: Database <br> Starting: Server <br> Compiling... <br> Ready!'
          break;
        case 2:
          document.getElementById('back-end').scrollIntoView();
          break;
        case 3:
          document.getElementById('databases').scrollIntoView();
          break;
        case 4:

          break;
        case 5:

          break;
      }
    }
  }
}
</script>

<style lang="scss">
  // General App styling
  body{
    margin: 0px;
    padding: 0px;
    white-space: nowrap;
    overflow: hidden;
  }

  //Component styling
  #app{
    .editor{
      position: fixed;
      right: 0px;
      top: 25vh;
    }
    .navigation_arrows{
      position: fixed;
    }
  }
</style>

<template>
  <div id="app">
    <div class="navigation_arrows">
      <button class="next" v-on:click="indexUp"><font-awesome-icon icon="chevron-down" /></button>
      <button class="prev" v-on:click="indexDown"><font-awesome-icon icon="chevron-up" /></button>
    </div>
    <home id="home"></home>
    <front-end id="front-end"></front-end>
    <back-end id="back-end"></back-end>
    <i-a id="ia"></i-a>
    <editor :code="codeText"></editor>
  </div>
</template>

<script>
// Imports
import Vue from 'vue'
import Home from './components/Home.vue';
import FrontEnd from './components/FrontEndDevelopment.vue';
import BackEnd from './components/BackEndDevelopment.vue';
import IA from './components/IndustrialAutomation.vue';
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
      maxIndex: 3,
    }
  },
  components: {
    Home,
    FrontEnd,
    BackEnd,
    IA,
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
    },
    checkPosition: function (index) {
      switch (index){
        case 0:
          document.getElementById('home').scrollIntoView({ block: 'end',  behavior: 'smooth' });
          this.codeText = 'root@portfolio: <span class="command">npm run portfolio</span> <br> Starting portfolio... <br> Starting: Database <br> Starting: Server <br> Compiling... <br> Ready!'
          break;
        case 1:
          document.getElementById('front-end').scrollIntoView({ block: 'end',  behavior: 'smooth' });
          this.codeText = '/* General Front end skills */ <br><br> .front-end{<br>&nbsp;&nbsp;styling: CSS, SASS, Less; <br>&nbsp;&nbsp;structure: HTML5, Jade; <br>&nbsp;&nbsp;frameworks: Bootstrap; <br>} <br><br> //Front end scripting skills <br><br> function mySkills(){ <br> &nbsp;&nbsp;var codeLanguages = {<br> &nbsp;&nbsp;&nbsp;general: ["Javascript", "JQuery", "JSON"], <br> &nbsp;&nbsp;&nbsp;frameworks: ["VueJS", "NodeJS"]<br>&nbsp;&nbsp;} <br> &nbsp;&nbsp;return codeLanguages; <br>}'
          break;
        case 2:
          document.getElementById('back-end').scrollIntoView({ block: 'end',  behavior: 'smooth' });
          this.codeText = '/* Back end skills */ <br><br> SELECT * FROM Skills WHERE Type = BackEnd <br><br> Query Result: <br><br> Name &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Type <br> PHP &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Code Language <br> MySQL &nbsp;&nbsp;&nbsp;&nbsp; Database Language <br> C &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Code Language <br> VBS &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Code Language <br> Wordpress &nbsp;CMS'
          break;
        case 3:
          document.getElementById('ia').scrollIntoView({ block: 'end',  behavior: 'smooth' });
          this.codeText = 'Sub IA_Skills(ByVal type) <br><br> Dim Skill <br><br> If (type = "PLC") Then <br> &nbsp;&nbsp;Set Skill = "Step 7" <br> &nbsp;&nbsp;Set Skill =  "TIA Portal" <br> End If <br><br> If (type = "SCADA") Then <br> &nbsp;&nbsp;Set Skill = "WinCC Classic" <br> &nbsp;&nbsp;Set Skill = "WinCC TIA Portal" <br> End If <br><br> If (type = "IIOT") Then <br> &nbsp;&nbsp;Set Skill = "Node Red"<br> End If <br><br> End Sub'
          break;
      }
    }
  },
  watch: {
    indexNumber: function (newIndex) {
      this.checkPosition(newIndex);
      localStorage.indexNumber = newIndex;
    }
  },
  mounted() {
    if (localStorage.indexNumber) {
      this.indexNumber = localStorage.indexNumber;
    }
    this.checkPosition(this.indexNumber);
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
      .next{
        position: fixed;
        bottom: 10px;
        left: 10px;
        font-size: 30px;
        background: none;
        border: none;
      }
      .prev{
        position: fixed;
        top: 10px;
        left: 10px;
        font-size: 30px;
        background: none;
        border: none;
      }
    }
  }
</style>

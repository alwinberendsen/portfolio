<template>
  <div id="app">
    <div class="navigation_arrows">
      <button class="next" v-on:click="indexUp"><font-awesome-icon icon="chevron-down" /></button>
      <div class="nav_indication">
        <ul>
          <li><span id='indicator_1'></span></li>
          <li><span id='indicator_2'></span></li>
          <li><span id='indicator_3'></span></li>
          <li><span id='indicator_4'></span></li>
        </ul>
      </div>
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
      codeText: [''],
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
          document.getElementById('indicator_1').classList.add('active');
          document.getElementById('indicator_2').classList.remove('active');
          this.codeText = ['root@portfolio: <span class="command">npm run portfolio</span> <br> Starting portfolio... <br> Starting: Database <br> Starting: Server <br> Compiling... <br> Ready!'];
          break;
        case 1:
          document.getElementById('front-end').scrollIntoView({ block: 'end',  behavior: 'smooth' });
          document.getElementById('indicator_2').classList.add('active');
          document.getElementById('indicator_1').classList.remove('active');
          document.getElementById('indicator_3').classList.remove('active');
          this.codeText = ['/* General Front end skills */ <br><br> .front-end{<br>&nbsp;&nbsp;styling: CSS, SASS, Less; <br>&nbsp;&nbsp;structure: HTML5, Jade; <br>&nbsp;&nbsp;frameworks: Bootstrap; <br>} <br><br> //Front end scripting skills <br><br> function mySkills(){ <br> &nbsp;&nbsp;var codeLanguages = {<br> &nbsp;&nbsp;&nbsp;general: ["Javascript", "JQuery", "JSON"], <br> &nbsp;&nbsp;&nbsp;frameworks: ["VueJS", "NodeJS"]<br>&nbsp;&nbsp;} <br> &nbsp;&nbsp;return codeLanguages; <br>}'];
          break;
        case 2:
          document.getElementById('back-end').scrollIntoView({ block: 'end',  behavior: 'smooth' });
          document.getElementById('indicator_3').classList.add('active');
          document.getElementById('indicator_2').classList.remove('active');
          document.getElementById('indicator_4').classList.remove('active');
          this.codeText = ['/* Back end skills */ <br><br> SELECT * FROM Skills WHERE Type = BackEnd <br><br> Query Result: <br><br> Name &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Type <br> PHP &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Code Language <br> MySQL &nbsp;&nbsp;&nbsp;&nbsp; Database Language <br> C &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Code Language <br> VBS &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Code Language <br> Wordpress &nbsp;CMS'];
          break;
        case 3:
          document.getElementById('ia').scrollIntoView({ block: 'end',  behavior: 'smooth' });
          document.getElementById('indicator_4').classList.add('active');
          document.getElementById('indicator_3').classList.remove('active');
          this.codeText = ['Sub IA_Skills(ByVal type) <br><br> Dim Skill <br><br> If (type = "PLC") Then <br> &nbsp;&nbsp;Set Skill = "Step 7" <br> &nbsp;&nbsp;Set Skill =  "TIA Portal" <br> End If <br><br> If (type = "SCADA") Then <br> &nbsp;&nbsp;Set Skill = "WinCC Classic" <br> &nbsp;&nbsp;Set Skill = "WinCC TIA Portal" <br> End If <br><br> If (type = "IIOT") Then <br> &nbsp;&nbsp;Set Skill = "Node Red"<br> End If <br><br> End Sub'];
          break;
      }
    }
  },
  watch: {
    indexNumber: function (newIndex) {
      this.checkPosition(newIndex);
      localStorage.indexNumber = newIndex;
    },
    codeText: function (newText) {
      localStorage.codeText = JSON.stringify(newText);
    }
  },
  mounted() {
    // Check local storage for previous values
    if (localStorage.indexNumber) {
      this.indexNumber = localStorage.indexNumber;
      this.checkPosition(localStorage.indexNumber);
    }
    if (localStorage.codeText) {
      this.codeText = JSON.parse(localStorage.codeText);
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
    font-family: Arial;
    h1{
      color: #C60021;
    }
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
        z-index: 2;
      }
      .prev{
        position: fixed;
        top: 10px;
        left: 10px;
        font-size: 30px;
        background: none;
        border: none;
        z-index: 2;
      }
      .nav_indication{
        min-height: 100vh;
        position: fixed;
        display: flex;
        flex-flow: row;
        align-items: center;
        vertical-align: middle;
        ul{
          padding: 0px;
          span{
            width: 35px;
            height: 2px;
            background-color: black;
            display: block;
            margin: 5px 10px;
            border-radius: 5px;
            -webkit-transition: all 0.2s;
            -moz-transition: all 0.2s;
            -ms-transition: all 0.2s;
            -o-transition: all 0.2s;
            transition: all 0.2s;
            &.active{
              height: 5px;
              width: 45px;
              background: #C60021;
            }
          }
        }
      }
    }
  }
</style>

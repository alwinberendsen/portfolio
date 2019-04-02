<template>
  <div id="app">
    <div class="part_home">
      <vue-particles color="#4bffa5" :particleOpacity="0.4" :particlesNumber="60" shapeType="circle" :particleSize="4" linesColor="#4bffa5" :lineOpacity="0.4"></vue-particles>
      <div class="text_content">
        <h1>Alwin Berendsen</h1>
        <p>Software Developer</p>
        <div class="btns">
          <a href="https://www.linkedin.com/in/alwin-berendsen-894170101/" class="btn-main" target="_blank">LinkedIn</a>
          <a href="https://github.com/alwinberendsen/portfolio" class="btn-main" target="_blank">Source code</a>
        </div>
      </div>
      <div class="skill_select">
        <ul>
          <li><span class="arrowPointer">></span><a v-on:click="indexNumber = 1">Front-End Development</a></li>
          <li><span class="arrowPointer">></span><a v-on:click="indexNumber = 2">Back-End Development</a></li>
          <li><span class="arrowPointer">></span><a v-on:click="indexNumber = 3">Industrial Automation</a></li>
        </ul>
      </div>
    </div>
    <editor :code="codeText" id="codeEditor"></editor>
  </div>
</template>

<script>
// Imports
import Vue from 'vue'
import editor from './components/Editor.vue';
import VueParticles from 'vue-particles';

Vue.use(VueParticles)

export default {
  name: 'app',
  data: function (){
    return {
      codeText: [''],
      indexNumber: 0,
      maxIndex: 3,
      loading: false,
    }
  },
  components: {
    editor
  },
  methods: {
    checkPosition: function (index) {
      document.getElementById('codeEditor').classList.add('open-Editor');
      switch (index){
        case 0:
          this.codeText = ['root@portfolio: <span class="command">npm run portfolio</span> <br> Starting portfolio... <br> Starting: Database <br> Starting: Server <br> Compiling... <br> Ready! Press the close button to start.'];
          break;
        case 1:
          this.codeText = ['/* General Front end skills */ <br><br> .front-end{<br>&nbsp;&nbsp;styling: CSS, SASS, Less; <br>&nbsp;&nbsp;structure: HTML5; <br>&nbsp;&nbsp;frameworks: Bootstrap; <br>} <br><br> //Front end scripting skills <br><br> function mySkills(){ <br> &nbsp;&nbsp;var codeLanguages = {<br> &nbsp;&nbsp;&nbsp;general: ["Javascript", "JQuery", "JSON"], <br> &nbsp;&nbsp;&nbsp;frameworks: ["VueJS", "NodeJS"]<br>&nbsp;&nbsp;} <br> &nbsp;&nbsp;return codeLanguages; <br>}'];
          break;
        case 2:
          this.codeText = ['/* Back end skills */ <br><br> SELECT * FROM Skills WHERE Type = BackEnd <br><br> Query Result: <br><br> Name &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Type <br> PHP &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Code Language <br> MySQL &nbsp;&nbsp;&nbsp;&nbsp; Database Language <br> C &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Code Language <br> VBS &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Code Language <br> Wordpress &nbsp;CMS'];
          break;
        case 3:
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
    this.checkPosition(0);

    // Check local storage for previous values
    if (localStorage.indexNumber) {
      //this.indexNumber = localStorage.indexNumber;
      //this.checkPosition(localStorage.indexNumber);
    }
    if (localStorage.codeText) {
      //this.codeText = JSON.parse(localStorage.codeText);
    }
  }
}
</script>

<style lang="scss">
  $blue: #040F3D;
  $mintGreen: #4BFFA5;

  $max-mobile: 500px;
  $max-tablet: 990px;
  $max-laptop: 1200px;
  // General App styling
  body{
    margin: 0px;
    padding: 0px;
    //white-space: nowrap;
    overflow: hidden;
    font-family: Arial;
    background: #fafafa;
    h1{
      color: $blue;
    }
  }

  //Component styling
  #app{
    //Home
    .part_home{
      //background: #f2f2f2bf;
      min-height: 100vh;
      min-width: 100%;
      // Center elements
      display: flex;
      flex-flow: row;
      align-items: center;
      vertical-align: center;

      @media screen and (max-width: $max-tablet){
        display: block;
      }

      //Particles effect
      #particles-js{
        position: absolute;
        top: 0px;
        z-index: 0;
        width: 100%;
        height: 100%;
      }

      // Text content
      .text_content{
        position: relative;
        z-index: 3;
        margin: 0px 10%;
        color: #C6C4C5;
        @media screen and (max-width: $max-tablet){
          margin: 0px 60px;
          margin-top: 100px;
        }
        @media screen and (max-width: $max-mobile){
          margin: 0px 20px;
          margin-top: 60px;
        }
        h1{
          margin: 0px;
          font-size: 45px;
          @media screen and (max-width: $max-mobile){
            font-size: 30px;
          }
        }
        p{
          font-size: 26px;
          margin: 0px;
          margin-bottom: 20px;
          @media screen and (max-width: $max-mobile){
            font-size: 20px;
          }
        }
        .btns{
          display: inline;
          .btn-main{
            display: inline-block;
            background: $mintGreen;
            padding: 10px 20px;
            -webkit-border-radius: 20px;
            -moz-border-radius: 20px;
            border-radius: 20px;
            margin-right: 20px;
            margin-top: 20px;
            color: $blue;
            -webkit-transition: all 0.3s;
            -moz-transition: all 0.3s;
            -ms-transition: all 0.3s;
            -o-transition: all 0.3s;
            transition: all 0.3s;
            text-decoration: none;
            &:hover{
              background: $blue;
              color: #fafafa;
            }
          }
        }
      }

      //Skill Select
      .skill_select{
        position: relative;
        z-index: 2;
        @media screen and (max-width: $max-tablet){
          margin: 0px 60px;
          margin-top: 100px;
        }
        @media screen and (max-width: $max-mobile){
          margin: 0px 20px;
          margin-top: 60px;
        }
        ul{
          list-style: none;
          padding: 0px;
          li{
            margin: 40px 0px;
            color: $blue;
            .arrowPointer{
              font-size: 40px;
              font-weight: 600;
              margin-right: 20px;
              @media screen and (max-width: $max-laptop){
                font-size: 30px;
              }
              @media screen and (max-width: $max-mobile){
                font-size: 20px;
              }
            }
            a{
              font-size: 40px;
              font-weight: 600;
              transition: all 0.2s;
              position: relative;
              background: transparent;
              z-index: 2;
              @media screen and (max-width: $max-laptop){
                font-size: 30px;
              }
              @media screen and (max-width: $max-mobile){
                font-size: 20px;
              }
              &:hover{
                background-color: $mintGreen;
                cursor: pointer;
              }
            }
          }
        }
      }
    }
    // Editor
    .editor {
      position: fixed;
      right: -800px;
      top: 0px;
      bottom: 0px;
      transition: all 0.5s;
      z-index: 3;
      &.open-Editor{
        right: 0px;
      }
    }

    // Responsive
    @media screen and (max-width: $max-mobile){

    }
  }
</style>

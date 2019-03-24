<template>
  <div id="app">
    <home></home>
    <front-end></front-end>
    <back-end></back-end>
    <databases></databases>
    <editor :code="codeText"></editor>
  </div>
</template>

<script>
import Home from './components/Home.vue';
import FrontEnd from './components/FrontEndDevelopment.vue';
import BackEnd from './components/BackEndDevelopment.vue';
import Databases from './components/Databases.vue';
import editor from './components/Editor.vue';

export default {
  name: 'app',
  data: function (){
    return {
      codeText: 'root@portfolio: npm run portfolio <br> Starting portfolio... <br> Starting: Database <br> Starting: Server <br> Compiling... <br> Ready!'
    }
  },
  components: {
    Home,
    FrontEnd,
    BackEnd,
    Databases,
    editor
  }

}
</script>

<style lang="scss">
  // General App styling
  body{
    margin: 0px;
    padding: 0px;
    white-space: nowrap;
  }

  //Component styling
  #app{
    .editor{
      position: fixed;
      right: 0px;
      top: 25vh;
    }
  }
</style>

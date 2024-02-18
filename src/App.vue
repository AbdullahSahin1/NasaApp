

<template>
  <div>
    <welcome-planet v-if="showWelcomeScreen"></welcome-planet>
    <ListWrapper v-else></ListWrapper>
  </div>
</template>

<script>
import ListWrapper from './components/ListWrapper.vue';
import WelcomePlanet from './components/WelcomePlanet.vue'
export default {
  data () {
    return {
      showWelcomeScreen : true
    }
  },
  created() {
    setTimeout(() => {
      document.body.style.padding = "20px"
      document.body.style.overflow = "auto" 
      this.showWelcomeScreen= false
    }, 0);
  },
  name: 'App',
  components: {
    WelcomePlanet,
    ListWrapper,
}
    
  
}
</script>

<style>
  *{
    font-family: Arial, Helvetica, sans-serif;
    margin: 0;
    background-color: #0b3d91;
    overflow: hidden;
  }
</style>

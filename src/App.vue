<template>
  <the-header>{{ msg }}</the-header>
  <the-character/> 
  <the-footer>{{ footer }}</the-footer>
  <router-view/>
</template>

<script>
import TheHeader from './components/TheHeader.vue'
import TheFooter from './components/TheFooter.vue'
import TheCharacter from './components/TheCharacter.vue'

export default {
  name: 'App',
  components: {
    TheHeader,
    TheFooter,
    TheCharacter
}
}
</script>

<style>
#app {
  font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body{
  margin: 0;
  background: linear-gradient( #ffffff, #0c0c11);;
}
</style>

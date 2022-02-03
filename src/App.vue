<template>
  <div id="app"> 
    <Header @srcInput="functionTest2"/>   
    <Main :searchValue="goSearch" />
  </div>
</template>

<script>
import Main from './components/Main.vue'
import Header from './components/Header.vue'

export default {
  name: 'App',

  components: {
    Main,
    Header
  },

  data(){
    return {
      goSearch: "",
    }
  },

  methods:{
    functionTest2(research2) {
      this.goSearch = research2
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/global.scss';
</style>

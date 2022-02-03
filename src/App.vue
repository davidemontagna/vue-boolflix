<template>
  <div id="app"> 
    <!--Dall'header recupero il valore passato con srcInput e con la funzione
    valueSearched inserisco il suo valore in goSearch che verrà passato al figlio (Main)
    come props-->
    <Header @srcInput="valueSearched"/>   
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
    //funzione per inserire il valore passato, dentro la variabile goSearch
    valueSearched(research2) {
      this.goSearch = research2
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/global.scss';
</style>

<template>
    <header class="dm-bg-header">
        <div class="container ">
            <div class="row">
                <div class="col-12 col-sm-6 col-lg-3 w-100 d-flex align-items-center justify-content-between">
                    <h2 class="dm-logo">
                        Boolflix
                    </h2>

                    <!--Inserirsco la searchbar e ne prendo il valore passato e mi preparo a passarlo
                    con una funzione al padre(App.vue)-->
                    <search-bar @searching="pastValue"/>

                </div>
            </div>
        </div>
    </header>
  
</template>

<script>
import SearchBar from './commons/SearchBar.vue';

export default {
    name: 'Header',
    components: {
        SearchBar
    },
    methods:{
        //funzione per passare con l'emit il valore ricevuto
        pastValue(research) {
            this.$emit('srcInput', research)
        }
    }
}
</script>

<style scoped lang="scss">
@import '../assets/style/global.scss';

.dm-bg-header{
    padding: 10px;
    background-color: $bg-header;
}

.dm-logo{
    margin: 0;
    font-weight: bold;
    font-size: 50px;
    color: $txt-logo-color;
    text-transform: uppercase;
}
</style>
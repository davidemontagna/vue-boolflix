<template>
    <header class="dm-bg-header">
        <div class="container-fluid ">
            <div class="row">
                <div class="col-12 col-sm-6 col-lg-3 w-100 d-flex align-items-center justify-content-between">
                    <div class="d-flex align-items-end justify-content-start dm-logo-menu">
                        <h2 class="dm-logo">
                        Boolflix
                        </h2>
                        <nav-menu />
                    </div>
                    

                   
                    <div class="dm-src-user d-flex align-items-center justify-content-evenly">
                        <!--Inserirsco la searchbar e ne prendo il valore passato e mi preparo a passarlo
                        con una funzione al padre(App.vue)-->
                        <search-bar @searching="pastValue"/>
                        <i class="fas fa-solid fa-bell dm-bell"></i>
                        <div class="dm-user d-flex align-items-center justify-content-between">
                            <img src="../assets/img/user-img/user-1.png" alt="">
                            <i class="fas fa-solid fa-caret-down dm-caret-down"></i>
                            <i class="fas fa-solid fa-caret-up dm-caret-up"></i>
                        </div>
                        
                    </div>
                    

                </div>
            </div>
        </div>
    </header>
  
</template>

<script>
import SearchBar from './commons/SearchBar.vue';
import NavMenu from './commons/NavMenu.vue'; 

export default {
    name: 'Header',
    components: {
        SearchBar,
        NavMenu
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
    font-size: 45px;
    color: $txt-logo-color;
    text-transform: uppercase;
}

.dm-logo-menu{
    width: 70%;
}

.dm-src-user{
    width: 30%;

    img{
        border-radius: 5px;
        height: 40px;
    }
}



.dm-bell{
    font-size: 30px;
    color: $txt-color-light;
    cursor: pointer;
}

.dm-user{
    width: 11%;
    cursor: pointer;

    .dm-caret-down, .dm-caret-up{
    font-size: 20px;
    color: $txt-color-light;
    }

    .dm-caret-up{
        display: none;
    }

    &:hover .dm-caret-down{
        display: none;
    }

    &:hover .dm-caret-up{
        display: block;
    }
}




</style>
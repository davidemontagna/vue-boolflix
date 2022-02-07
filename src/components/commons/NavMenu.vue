<template>
    <nav class="dm-menu">
        <ul class="d-flex align-items-center justify-content-evenly">
            <li 
            v-for="(element, index) in menuList" 
            :key="index">
            <a href="#">{{element}}</a>
            </li>
        </ul>
    </nav>
  
</template>

<script>
export default {
    name: 'NavMenu',
    data(){
        return{
            menuList: ['Home', 'Series', 'Films', 'New & Popular', 'My List']
        }
    }
}
</script>

<style scoped lang="scss">
@import '../../assets/style/global.scss';

nav{
    width: 35%;
}

.dm-menu{
    width: 35%;
    margin-bottom: 0;

    li{
        list-style: none;
        color: $txt-color-light;        

        a{
            text-decoration: none;
            color: $txt-color-light;

            &:hover{
                color: rgb(179, 176, 176);
            }
        }
    }
    
}
</style>
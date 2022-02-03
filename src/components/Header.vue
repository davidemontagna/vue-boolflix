<template>
    <header class="dm-bg-header">
        <div class="container ">
            <div class="row">
                <div class="col-12 col-sm-6 col-lg-3 w-100 d-flex align-items-center justify-content-between">
                    <h2 class="dm-logo">
                        Boolflix
                    </h2>

                    <search-bar @searching="functionTest"/>

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
        functionTest(research) {
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
</style>
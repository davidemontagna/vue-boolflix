<template>
    <header>
        <div class="container">
            <div class="row">
                <div class="col-12 col-sm-6 col-lg-3">

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

<style>

</style>
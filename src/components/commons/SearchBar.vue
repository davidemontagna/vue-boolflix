<template>
    <div>
        <input 
        type="text"
        v-model.trim="search"
        @keyup.enter="$emit('searching', search), clearInput()"
        >

        <button
        value="go-search"
        @click="$emit('searching', search), clearInput()"
        >        
        Search
        </button>

    </div>
</template>

<script>
export default {
    name: 'SearchBar',
    data(){
        return {
            search: "",
        }
    },

    methods:{
        clearInput(){
            this.search = "";
        }
    }
}
</script>

<style>

</style>
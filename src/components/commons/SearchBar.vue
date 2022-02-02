<template>
    <div>
        <input type="text" v-model="search">

        <button
        value="go-search"
        @click="$emit('searching', search)"
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
    }
}
</script>

<style>

</style>
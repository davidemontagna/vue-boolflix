<template>
    <div>
        <input
        class="dm-src-bar" 
        type="text"
        v-model.trim="search"
        @keyup.enter="$emit('searching', search), clearInput()"
        >

        <button
        class="dm-btn-research"
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

<style scoped lang="scss">
@import '../../assets/style/global.scss';

.dm-src-bar{
    border-radius: 20px;
    padding: 5px 15px;
    width: 270px;
}

.dm-btn-research{
    margin-left: 10px;
    padding: 5px 10px;
    background-color: $bg-buttons;
    color: $txt-color-light;
    border-radius: 20px;
}
</style>
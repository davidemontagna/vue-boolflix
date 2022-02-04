<template>
    <div>
        <!--Input per la ricerca del film e serie tv, con l'emit lo passo al padre(Header)-->
        <input
        class="dm-src-bar" 
        type="text"
        v-model.trim="search"
        @keyup.enter="$emit('searching', search), clearInput()"
        placeholder="Title"
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
        
        //Funzione per ripulire l'input text una volta premuto invio o al click sul bottone
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
<template>
    <main>
        <search-bar @searching="startSearch"/>
        main
    </main>
</template>

<script>
import axios from 'axios';
import SearchBar from './commons/SearchBar.vue';

export default {
    name: 'Main',
    components: {
        SearchBar,
    },

    data(){
        return {
            apiURL: "https://api.themoviedb.org/3/search/movie/",
            api: "73c18d57cad03bbd2fde6c0db5157c10",
            arrayMovies: [],
            movieSearched: ""
        }
    },

    

    methods: {
        getMovie() {
            axios
                .get(this.apiURL, {
                    params: {
                        api_key: this.api,
                        query: this.movieSearched
                    }
                })
                .then( (response) => {
                    this.arrayMovies = response.data.results
                    console.log(this.arrayMovies)
                })
                .catch(function (error) {
                    console.log(error);
                })
        },

        startSearch(search){
            this.movieSearched = search;
            this.getMovie()            
        }
    }
}
</script>

<style>

</style>
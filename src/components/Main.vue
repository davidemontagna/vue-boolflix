<template>
    <main>
        <search-bar @searching="startSearch"/>
        <div class="container">
            <div class="row">
                <h2>Lista Film:</h2>
                <div class="col-12 col-sm-6 col-lg-3 w-100 d-flex justify-content-start flex-wrap">
                    
                    <movie 
                    v-for="movie in arrayMovies"
                    :key="movie.id"
                    :movie="movie"
                    />
                    
                </div>
                <h2 class="mt-5">Lista Serie TV:</h2>
                <div class="col-12 col-sm-6 col-lg-3 my-3 w-100 d-flex justify-content-start flex-wrap">
                    
                    <tv-serie 
                    v-for="TvSerie in arrayTvSeries"
                    :key="TvSerie.id"
                    :TvSerie="TvSerie"
                    />
                    
                </div>
            </div>
        </div>
        
    </main>
</template>

<script>
import axios from 'axios';
import SearchBar from './commons/SearchBar.vue';
import Movie from './commons/Movie.vue';
import TvSerie from './commons/TvSerie.vue';

export default {
    name: 'Main',
    components: {
        SearchBar,
        Movie,
        TvSerie
    },

    data(){
        return {
            apiUrlMovie: "https://api.themoviedb.org/3/search/movie/",
            apiUrlTvSeries: "https://api.themoviedb.org/3/search/tv",
            api: "73c18d57cad03bbd2fde6c0db5157c10",
            arrayMovies: [],
            arrayTvSeries: [],
            movieSearched: "",
            tvSerieSearched: ""
        }
    },

    methods: {
        getMovie() {
            axios
                .get(this.apiUrlMovie, {
                    params: {
                        api_key: this.api,
                        query: this.movieSearched
                    }
                })
                .then( (response) => {                    
                    this.arrayMovies = response.data.results;
                    console.log(this.arrayMovies);
                })
                .catch(function (error) {
                    console.log(error);
                })
        },

        getTvSeries() {
            axios
                .get(this.apiUrlTvSeries, {
                    params: {
                        api_key: this.api,
                        query: this.tvSerieSearched
                    }
                })
                .then( (response) => {                    
                    this.arrayTvSeries = response.data.results;
                    console.log(this.arrayTvSeries);
                })
                .catch(function (error) {
                    console.log(error);
                })
        },

        

        startSearch(search){
            this.tvSerieSearched = search;
            this.movieSearched = search;
            this.getMovie();
            this.getTvSeries();     
        }
    }
}
</script>

<style scoped lang="scss">
@import '../assets/style/global.scss';

main{
    width: 100vw;
}
</style>
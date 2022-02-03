<template>
    <main>        
        <div class="container" :class="getArraySearched">
            <div class="row">
                
                <div v-show="arrayMovies != ''"
                class="col-12 col-sm-6 col-lg-3 w-100 flex-column justify-content-start flex-wrap">
                    
                    <div class="justify-content-start">
                        <h2>Lista Film:</h2>
                    </div>
                    <div class="d-flex justify-content-start flex-wrap">
                        <movie 
                        v-for="movie in arrayMovies"
                        :key="movie.id"
                        :movie="movie"
                        />
                    
                    </div>                   
                </div>

                
                <div v-show="arrayMovies != ''"
                class="col-12 col-sm-6 col-lg-3 my-3 w-100 flex-column justify-content-start flex-wrap">
                    
                    <div class="justify-content-start">
                        <h2>Lista Serie Tv:</h2>
                    </div>
                    <div class="d-flex justify-content-start flex-wrap">
                        <tv-serie 
                        v-for="TvSerie in arrayTvSeries"
                        :key="TvSerie.id"
                        :TvSerie="TvSerie"
                        />                    
                    </div>

                </div>
            </div>
        </div>
        
    </main>
</template>

<script>
import axios from 'axios';
import Movie from './commons/Movie.vue';
import TvSerie from './commons/TvSerie.vue';

export default {
    name: 'Main',
    components: {        
        Movie,
        TvSerie
    },
    props:{
        searchValue: String,
    },

    data(){
        return {
            apiUrlMovie: "https://api.themoviedb.org/3/search/movie/",
            apiUrlTvSeries: "https://api.themoviedb.org/3/search/tv",
            myApi: "73c18d57cad03bbd2fde6c0db5157c10",
            arrayMovies: [],
            arrayTvSeries: [],
            movieSearched: "",
            tvSerieSearched: ""
        }
    },    

    computed:{
        getArraySearched(){
            if(this.searchValue != ""){
                this.getMovie()
                this.getTvSeries()
                return this.searchValue;
            }
            return "";
        }
    },

    methods: {
        getMovie() {
            
            axios
                .get(this.apiUrlMovie, {
                    params: {
                        api_key: this.myApi,
                        query: this.searchValue
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
                        api_key: this.myApi,
                        query: this.searchValue
                    }
                })
                .then( (response) => {                    
                    this.arrayTvSeries = response.data.results;
                    console.log(this.arrayTvSeries);
                })
                .catch(function (error) {
                    console.log(error);
                })
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
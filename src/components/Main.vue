<template>
    <main>        
        <div class="container" :class="getArraySearched">
            <div class="row">
                
                <div v-show="arrayMovies != ''"
                class="col-12 col-sm-6 col-lg-3 mt-4 w-100 flex-column justify-content-start flex-wrap">
                    
                    <div class="justify-content-start">
                        <h1 class="dm-list-txt">Lista Film:</h1>
                    </div>
                    <div class="d-flex justify-content-evenly flex-wrap">
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
                        <h1 class="dm-list-txt">Lista Serie Tv:</h1>
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

    //Recupero il valore passato dal padre (App.vue) e gli do String come type
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
        }
    },    

    //al cambio di valore nell'imput getArraySearched esegue le funzioni getMovie e getTvSeries
    //e restituisce il valore da ricercare
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
        //axios per generare l'API da cui prendere il mio array di oggetti (in questo caso film)
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

        //axios per generare l'API da cui prendere il mio array di oggetti (in questo caso serie tv)
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
    background-color: $bg-main;
    width: 100vw;
    min-height: calc(100vh - 74px);
}

.dm-list-txt{
    color: $txt-color-light;
}
</style>
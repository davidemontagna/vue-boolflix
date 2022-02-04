<template>
    <div class="card my-2 mx-2">
        <img :src="img + movie.poster_path" alt="unknown">
        <ul class="mt-2">
            <li>
            <span>Titolo film: </span> <h4>{{movie.title}}</h4> <br>
            <span>Titolo originale: </span>{{movie.original_title}} <br>
            <span>Lingua originale: </span>
                <img 
                class="flag-lang"
                :src="require(`../../assets/img/flags/${flag(movie.original_language)}.png`)" 
                :alt="movie.original_language"> 
                <br>                
                <span>Media voto: </span>
                <span :class="starVote()"
                v-for="index in stars"
                :key="index"
                >
                {{index}}
                </span>{{movie.vote_average}}
            </li> 
        </ul>      
    </div>
    
</template>

<script>
export default {
    name: 'Movie',
    props: {
        movie: Object,
    },
    data(){
        return {
            img: "https://image.tmdb.org/t/p/w342",
            langArray: ['en', 'it', 'es'],
            stars: this.starVote(),

        }
    },
    methods: {
        flag(lang){
            let urlFlag = "horde";
            if(this.langArray.includes(lang)){
                urlFlag = lang;
            }
            return urlFlag
        },

        starVote(){            
            let starVote = Math.ceil(this.movie.vote_average / 2);            
            console.log(starVote)
        }
    }
     
    
}
</script>

<style scoped lang="scss">
 @import '../../assets/style/global.scss';

.flag-lang{
    height: 20px;
}

.card{
    min-height: 500px;    
    width: 230px;
    padding: 10px;
    border: 1px solid #000;

    & ul{  
        padding: 0;      
        list-style: none;

        li{
            font-weight: bold;

            span{
                font-size: 15px;
                font-weight: lighter;
            }
        }

        
    }
}
</style>
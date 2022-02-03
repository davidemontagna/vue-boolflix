<template>
    <div class="card my-2 mx-2">
        <img :src="img + movie.poster_path" alt="unknown">
        <ul>
            <li>
            <span>Titolo film: </span> <h4>{{movie.title}}</h4> <br>
            <span>Titolo originale: </span>{{movie.original_title}} <br>
            <span>Lingua originale: </span>
                <img 
                v-if="movie.original_language == 'en'"
                src="../../assets/img/flags/usa-flag.png"
                alt="en"
                class="flag-lang"
                >
                <img 
                v-else-if="movie.original_language == 'it'"
                src="../../assets/img/flags/ita-flag.png"
                alt="it"
                class="flag-lang"
                >
                <img 
                v-else-if="movie.original_language == 'es'"
                src="../../assets/img/flags/es-flag.jpg"
                alt="es"
                class="flag-lang"
                >           
                <img 
                v-else
                src="../../assets/img/flags/horde-flag.png"
                alt="unknown"
                class="flag-lang"
                ><br>                
                <span>Media voto: </span>{{movie.vote_average}}
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
        }
    },
     
    
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
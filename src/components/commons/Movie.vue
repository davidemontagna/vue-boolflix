<template>
    <div class="card my-2 mx-2 dm-card position-relative">
        <img class="dm-poster dm-moving-left" :src="img + movie.poster_path" alt="unknown">
        <ul class="mt-2 dm-details">
            <li>
            <span>Titolo film: </span> <h4>{{movie.title}}</h4>
            <span>Titolo originale: </span>{{movie.original_title}} <br>
            <span>Lingua originale: </span>
                <img 
                class="flag-lang"
                :src="require(`../../assets/img/flags/${flag(movie.original_language)}.png`)" 
                :alt="movie.original_language"> 
                <br>                
                <span>Media voto: 
                    <span                     
                    v-for="index in starVote(movie.vote_average)"
                    :key="index"
                    >
                    <img class="stars" src="../../assets/img/star/star.png" alt="">
                    </span> 
                </span><br>
                <span>Descrizione:</span> <p>{{movie.overview}}</p>
                
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

        starVote(vote){            
            vote = Math.ceil(this.movie.vote_average / 2);
                        
            
            return vote
        },

        
    }
     
    
}
</script>

<style scoped lang="scss">
 @import '../../assets/style/global.scss';

.flag-lang{
    height: 20px;
}

.dm-card{
    background-color: #000!important;
    overflow-x: hidden;
    overflow-y: scroll;
    width: 230px;
    padding: 10px;
    border: 1px solid #000!important;
    border-radius: 10px!important;

    &::-webkit-scrollbar{
        display: none;
    }

    &:hover .dm-details{
        display: block;
        opacity: 1;        
        transition: 1.8s ease-in;
    }

    .dm-poster{
        position: relative;
        transition: transform 1.5s;
        transform: translateX(0px);
    }

    &:hover .dm-poster{
        transform: translateX(-500px);        
    }

    & ul{  
        padding: 0;      
        list-style: none;

        li{
            font-weight: lighter;
            color: $txt-color-light;

            span{
                font-size: 15px;
                font-weight: bold;                
            }

            p{
                font-size: 13px;
                font-weight: lighter;
            }
        }

        
    }
}

.dm-details{
    opacity: 0; 
    transition: .8s ease-out;
    position: absolute;
    top: 10px;
    left: 10px;
}

.stars{
    height: 15px;
}
</style>
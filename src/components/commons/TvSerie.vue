<template>
    <div class="card my-2 mx-2 dm-card position-relative">
        <img class="dm-poster dm-moving-left" :src="img + TvSerie.poster_path" alt="unknown">
        <ul class="mt-2 dm-details">
            <li>
            <span>Titolo serie tv: </span> <h4>{{TvSerie.name}}</h4> <br>
            <span>Titolo originale: </span>{{TvSerie.original_name}} <br>
            <span>Lingua originale: </span>
                <img 
                class="flag-lang"
                :src="require(`../../assets/img/flags/${flag(TvSerie.original_language)}.png`)"
                :alt="TvSerie.original_language"
                ><br>                
                <span>Media voto: 
                    <span                     
                    v-for="index in starVote(TvSerie.vote_average)"
                    :key="index"
                    >
                    <img class="stars" src="../../assets/img/star/star.png" alt="">
                    
                    </span>
                </span>
            </li> 
        </ul>      
    </div>
    
</template>

<script>
export default {
    name: 'TvSerie',
    props: {
        TvSerie: Object,
    },
    data(){
        return {
            img: "https://image.tmdb.org/t/p/w342",
            langArray: ['en', 'it', 'es'],
        }
    }, 
    methods:{
        flag(lang){
            let urlFlag = "horde";
            if(this.langArray.includes(lang)){
                urlFlag = lang;
            }
            return urlFlag
        },

        starVote(vote){            
            vote = Math.ceil(this.TvSerie.vote_average / 2);        
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
    overflow: hidden;
    width: 230px;
    padding: 10px;
    border: 1px solid #000!important;
    border-radius: 10px!important;

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
            font-weight: bold;
            color: $txt-color-light;

            span{
                font-size: 15px;
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
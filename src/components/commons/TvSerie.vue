<template>
    <div class="card my-2 mx-2">
        <img :src="img + TvSerie.poster_path" alt="unknown">
        <ul>
            <li>
            <span>Titolo serie tv: </span> <h4>{{TvSerie.name}}</h4> <br>
            <span>Titolo originale: </span>{{TvSerie.original_name}} <br>
            <span>Lingua originale: </span>
                <img 
                class="flag-lang"
                :src="require(`../../assets/img/flags/${flag(TvSerie.original_language)}.png`)"
                :alt="TvSerie.original_language"
                ><br>                
                <span>Media voto: </span>{{TvSerie.vote_average}}
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
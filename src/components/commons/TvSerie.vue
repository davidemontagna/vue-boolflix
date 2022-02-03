<template>
    <div class="card my-2 mx-2">
        <ul>
            <li>
            <span>Titolo serie tv: </span> <h4>{{TvSerie.name}}</h4> <br>
            <span>Titolo originale: </span>{{TvSerie.original_name}} <br>
            <span>Lingua originale: </span>
                <img 
                v-if="TvSerie.original_language == 'en'"
                src="../../assets/img/flags/usa-flag.png"
                alt="en"
                class="flag-lang"
                >
                <img 
                v-else-if="TvSerie.original_language == 'it'"
                src="../../assets/img/flags/ita-flag.png"
                alt="it"
                class="flag-lang"
                >
                <img 
                v-else-if="TvSerie.original_language == 'es'"
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
    }    
    
}
</script>

<style scoped lang="scss">
 @import '../../assets/style/global.scss';

.flag-lang{
    height: 20px;
}

.card{
    height: 350px;
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
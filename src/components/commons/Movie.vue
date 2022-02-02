<template>
    <div>
       <h3>Titolo film: {{movie.title}}</h3> 
       <span>Titolo originale: {{movie.original_title}}</span> <br>
       <span>
           Lingua originale: 
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
           >
        </span> <br>
       <span>Media voto: {{movie.vote_average}}</span> <br>
       
    </div>
</template>

<script>
export default {
    name: 'Movie',
    props: {
        movie: Object,
    }    
    
}
</script>

<style scoped lang="scss">
.flag-lang{
    height: 20px;
}
</style>
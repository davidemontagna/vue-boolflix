<template>
    <div>
       <h3>Titolo film: {{movie.title}}</h3> 
       <span>Titolo originale: {{movie.original_title}}</span> <br>
       <span>Lingua originale: {{movie.original_language}}</span> <br>
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

<style>

</style>
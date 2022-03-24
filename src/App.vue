<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import { ref } from "vue";
import HelloWorld from './components/HelloWorld.vue'
import FilmCard from './components/FilmCard.vue'
import FilmInfo from './components/FilmInfo.vue'

const filmData = ref(null);

const activeFilm = ref(0);


fetch("https://ghibliapi.herokuapp.com/films")
    .then((response) => response.json())
    .then(data => filmData.value = data)

const filmCardClick = (i) => {
    activeFilm.value = i;
}
</script>

<template>
        <nav class="films-list">
            <FilmCard v-for="(film, i) in filmData"
            :key="'film'+i"
            :filmTitle="film.title"
            :imageSrc="film.movie_banner"
            :filmDirector="film.director"
            @click="filmCardClick(i)"/>
        </nav>
<film-info
    :filmTitle="filmData[activeFilm].title"
    :filmTitleOriginal="filmData[activeFilm].original_title"
    :filmYear="filmData[activeFilm].release_date"
    :filmDirector="filmData[activeFilm].director"
    :filmImage="filmData[activeFilm].image"
    :filmDescription="filmData[activeFilm].description"
    />
</template>

<style>

body {
    margin: 0;
    background: black;
    color: white;
}

img {
    width: 100%;
    height: 300px;
}

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    display: flex;
}
</style>

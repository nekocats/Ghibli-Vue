<script setup>

defineProps ({
    filmTitle: String,
    filmTitleOriginal: String,
    filmDirector: String,
    filmYear: String,
    filmImage: String,
    filmDescription: String
})

</script>
<template>
    <div class="film-info">
        <img :src="filmImage" class="film-image">

        <div class="filminfo-container">

            <h1 class="film-titles">{{filmTitle}} <span>{{filmTitleOriginal}}</span></h1>
            <div class="extra-info">
            <span class="film-year">release date : <em>{{filmYear}}</em></span>
            <p class="film-director">Director : <em>{{filmDirector}}</em></p>
            </div>
            <p class="film-description">{{filmDescription}}</p>
        </div>
    </div>
</template>
<style>
.film-titles {
    display: flex;
    flex-direction: column;
}

.filminfo-container{
    padding: 0px 3rem;
}

.extra-info {
    font-size: 20px;
    gap: 2rem;
    display: flex;
}

.film-director {
    margin: 0;
}

.film-description {
    margin: 3rem 0px;
}

.film-info {
    padding: 5vh 2rem 5vh 2rem;
    position: sticky;
    top: 0;
    left: 0;
    height: 100%;
    width: 1fr;
    display: flex;
}
.film-image {
    border-radius: 20px;
    width: auto;
    height: 90vh;
}
</style>

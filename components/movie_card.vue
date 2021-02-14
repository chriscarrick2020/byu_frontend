<template>
    <div class="movie-card-container">
        <div class="movie-card-header"><h2>{{ movie.title }}</h2></div>
        <div class="movie-card-content">
            <div class="movie-poster-img" v-if="movie.poster_image_url">
                <img v-bind:src="movie.poster_image_url" alt="" srcset="">
            </div>
            <div class="movie-poster-img" v-else></div>
            <div class="text-container">
                <div class="text">{{ movie.popularity_summary }}</div>
                <div class="text">TMDB ID: {{ movie.movie_id }}</div>
            </div>

        </div>
    </div>
</template>

<script>
export default {
    props: {
        movie: {type: Object, default: function() { return {} }}
    }
}
</script>

<style>
.movie-card-container {
    width: 300px;
    margin: 10px;
    background-color: #E27D60;
    border-radius: 10px;
}

.movie-card-header {
    background-color: #C38D9E;
    padding: 10px;
    color: white;
    height: 100px;
    display: flex;
    justify-content: center;
    align-content: center;
    align-items: center;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
}

h2 {
    font-size: 20px;
    letter-spacing: 2px;
}

.movie-poster-img {
    height: 390px;
    background-color: black;
    border-radius: 10px;
}

.movie-poster-img img {
    max-width: 100%;
    border-radius: 10px;
}

.movie-card-content {
    padding: 20px;
    width: 100%;
    margin: 0px;
    display: flex;
    flex-direction: column;
}

.text-container {
    display: flex;
    flex-direction: column;
}

.text {
    color: white;
    padding-top: 10px;
}

</style>
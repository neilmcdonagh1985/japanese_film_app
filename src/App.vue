<template>
  <div>
    <h1>Film App</h1>
    <div>
      <film-detail :film='selectedFilm'></film-detail>
      <film-list :films='films'></film-list>
    </div>
  </div>
  
</template>

<script>

import FilmList from './components/FilmList.vue';
// import FilmItem from './components/FilmItem.vue';
import FilmDetail from './components/FilmDetail.vue';
import { eventBus } from './main.js';


export default {
  name: 'app',
  data(){
    return {
      films: [],
      selectedFilm: null
    };
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(films => this.films = films)

    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film
    })


  },
  components: {
    'film-list': FilmList,
    'film-detail': FilmDetail
  }

}
</script>

<style>

</style>
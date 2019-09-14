<template>
  <div>
    <h1>Film App</h1>
    <div>
      <film-detail :film='selectedFilm'></film-detail>
      <film-list :films='films'></film-list>
    </div>
    <films-to-watch-later :filmsToWatchLater='filmsToWatchLater'></films-to-watch-later>
  </div>
  
</template>

<script>

import FilmList from './components/FilmList.vue';
import FilmItem from './components/FilmItem.vue';
import FilmDetail from './components/FilmDetail.vue';
import FilmsToWatchLater from './components/FilmsToWatchLater.vue'
import { eventBus } from './main.js';


export default {
  name: 'app',
  data(){
    return {
      films: [],
      selectedFilm: null,
      filmsToWatchLater: []
    };
  },
  methods: {
    markToWatch: function(film){
      const idsOfWatchLaterList = (this.filmsToWatchLater.map(film => film.id))
      if (!this.isOnWatchLaterList(film)) this.filmsToWatchLater.push(film)
    },
    isOnWatchLaterList: function(film){
      const idsOfWatchLaterList = (this.filmsToWatchLater.map(film => film.id))
      return idsOfWatchLaterList.includes(film.id)
    }
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(films => this.films = films),

    eventBus.$on('film-selected', film => this.selectedFilm(film));
    eventBus.$on('film-to-watch-later', film => this.markToWatch(film));
  },
  components: {
    "film-list": FilmList,
    "film-detail": FilmDetail,
    "film-item": FilmItem,
    "films-to-watch-later": FilmsToWatchLater
  },
  }

</script>

<style lang='css' scoped>

</style>
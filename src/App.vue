<template>
  <div id="app">
    <h1>Film App</h1>
    <div id="list-info">
      <film-list :films='films' :favourites='favourites'></film-list>
      <film-detail :film='selectedFilm'></film-detail>
      <films-to-watch-later :filmsToWatchLater='filmsToWatchLater'></films-to-watch-later>
    </div>
  </div>
  
</template>

<script>
import FilmList from './components/FilmList.vue';
import FilmItem from './components/FilmItem.vue';
import FilmDetail from './components/FilmDetail.vue';
import FilmsToWatchLater from './components/FilmsToWatchLater.vue';
import WatchLaterListItem from './components/WatchLaterListItem.vue';
import { eventBus } from './main.js';


export default {
  name: 'app',
  data(){
    return {
      films: [],
      selectedFilm: null,
      filmsToWatchLater: [],
      favourites: []
    };
  },
  methods: {
    markToWatch: function(film){
      const idsOfWatchLaterList = (this.filmsToWatchLater.map(filmToWatchLater => filmToWatchLater.id))
      if (!this.isOnWatchLaterList(film)) this.filmsToWatchLater.push(film)
    },
    unmarkToWatch: function(film){
      const index = this.filmsToWatchLater.indexOf(film);
      this.filmsToWatchLater.splice(index, 1)
    },
    isOnWatchLaterList: function(film){
      const idsOfWatchLaterList = (this.filmsToWatchLater.map(filmToWatchLater => filmToWatchLater.id))
      return idsOfWatchLaterList.includes(film.id)
    }
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(films => this.films = films),

    eventBus.$on('film-selected', film => this.selectedFilm = film);
    eventBus.$on('film-to-watch-later', film => this.markToWatch(film));
    eventBus.$on('item-removed', film => this.unmarkToWatch(film));
    eventBus.$on('favourite-selected', film => this.favourites.push(film));
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

h1 {
  justify-content: center;
  display: flex;
}

 #list-info {
  display: flex;
} 

#app {
  color: lightsalmon;
  background-color: black;
  font-family: -apple-system, BlinkMacSystemFont, 
  'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 
  'Open Sans', 'Helvetica Neue', sans-serif;
}

</style>
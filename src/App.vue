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
import FilmItem from './components/FilmItem.vue';
import FilmDetail from './components/FilmDetail.vue';
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
  // methods: {
  //   markTowatchLater: function(beer){
  //     filmsToWatchLater.push(beer)
  //   }
  // },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(films => this.films = films)

    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film
    }),
    eventBus.$on('film-to-watch-later', (film) => {
      this.selectedFilm = film
      this.filmsToWatchLater.push(this.selectedFilm)
    })
    },

  components: {
    'film-list': FilmList,
    'film-detail': FilmDetail,
    'film-item': FilmItem
  }

}
</script>

<style>

</style>
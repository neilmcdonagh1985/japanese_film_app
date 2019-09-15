<template lang='html'>
  <div id="film-item">
  <li :class="{'favourite': favourites.includes(film)}">{{film.title}}</li>
  <button v-on:click='displayInfo'>Details</button>
  <button v-on:click='addToWatchLater'>add to watch later</button>
  <button v-on:click='markAsFavourite'>Favourite</button>
  </div>
  
</template>

<script>
import { eventBus } from '../main.js'
// import FilmList from '../App.vue';

export default {
    name: 'film-item',
    props: ['film', 'favourites'],
    methods: {
        displayInfo: function(){
            eventBus.$emit('film-selected', this.film);
        },
        addToWatchLater: function(){
            // IsOnWatchLaterList(this.film);
            eventBus.$emit('film-to-watch-later', this.film);

        },
        markAsFavourite(){
            eventBus.$emit('favourite-selected', this.film);
        }
    }


}
</script>

<style lang='css' scoped>

  #film-item{
    padding: 10px;
}

li {
    font-family: -apple-system, BlinkMacSystemFont, 
  'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 
  'Open Sans', helvetica Neue, sans-serif;
  font-weight: bold; 
}

.favourite {
    border: 2px solid aquamarine
}

button {
    margin: 10px;
    border: 2px solid lightsalmon;
}

</style>
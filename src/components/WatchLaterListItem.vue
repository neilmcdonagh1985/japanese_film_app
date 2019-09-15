<template lang='html'>
  <li>
      {{filmToWatchLater.title}}
      <button v-on:click="removeFromWatchList">Watched</button>
  </li>
  
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'watch-later-listitem',
    props: ['filmToWatchLater', 'filmsToWatchLater'],
    methods: {
        removeFromWatchList: function(){
            eventBus.$emit('item-removed', this.film);
        }
    } 


}
</script>

<style lang='css' scoped>
 li {
     padding: 10px;
     font-family: -apple-system, BlinkMacSystemFont, 
  'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 
  'Open Sans', 'Helvetica Neue', sans-serif;
  font-weight: bold;
 }

 button {
     border: 2px solid lightsalmon;
 }


</style>
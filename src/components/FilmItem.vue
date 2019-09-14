<template lang='html'>
  <div>
  <li>{{film.title}}</li>
  <button v-on:click='displayInfo'>Details</button>
  <button v-on:click='addToWatchLater'>add to watch later</button>
  </div>
  
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'film-item',
    props: ['film'],
    methods: {
        displayInfo: function(){
            eventBus.$emit('film-selected', this.film);
        },
        addToWatchLater: function(){
            eventBus.$emit('film-to-watch-later', this.film);

        }
    }


}
</script>

<style lang='css' scoped>

</style>
<template lang='html'>
  <div id="film-item">
  <li>{{film.title}}</li>
  <button v-on:click='displayInfo'>Details</button>
  <button v-if='' v-on:click='addToWatchLater'>add to watch later</button>
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
            // IsOnWatchLaterList(this.film);
            eventBus.$emit('film-to-watch-later', this.film);

        }
    }


}
</script>

<style lang='css' scoped>
#film-item{
    display: flex;
}

</style>
<template lang='html'>
  <div>
  <li>{{film.title}}</li>
  <button v-on:click='displayInfo'>add to watched list</button>
  </div>
  
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'film-item',
    props: ['film'],
    methods: {
        displayInfo(){
            eventBus.$emit('film-selected', this.film)
        }
    }


}
</script>

<style lang='css' scoped>

</style>
<template lang='html'>
  <li>{{film.title}}</li>
  
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'film-item',
    props: ['film'],
    methods: {
        handleClick(){
            eventBus.emit('film-selected', this.film)
        }
    }


}
</script>

<style lang='css' scoped>

</style>
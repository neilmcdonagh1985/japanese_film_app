<template lang='html'>
  <div id="film-list">
    <ul style="list-style: none;">
      <film-item v-for='film in films' :film='film' :key='film.id'></film-item>
    </ul>

  </div>

  
</template>

<script>
import FilmItem from './FilmItem'


export default {
    name: 'film-list',
    props: ['films'],
    components: {
        'film-item': FilmItem
    }

}
</script>

<style lang='css' scoped>
#film-list {
    background-color: black;
    width: 40%;
    color: lightsalmon;
}


</style>
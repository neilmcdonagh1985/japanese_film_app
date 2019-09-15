<template lang='html'>
  <div id="film-list">
    <ul>
      <film-item v-for='(film, index) in films' :film='film' :key='index'></film-item>
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

</style>
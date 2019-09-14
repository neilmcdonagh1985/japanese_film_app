<template lang='html'>
  <div id="watch-later-list">
    <ul>
      <watch-later-listitem v-for='(filmToWatchLater, index) in filmsToWatchLater' 
        :filmToWatchLater='filmToWatchLater'
        :key='index'
        ></watch-later-listitem>
    </ul>
  </div>  
</template>

<script>

import WatchLaterListitem from './WatchLaterListItem'

export default {
    name: 'films-to-watch-later',
    props: ['filmsToWatchLater'],
    components: {
        'watch-later-listitem': WatchLaterListitem
    }

}
</script>

<style lang='css' scoped>

</style>
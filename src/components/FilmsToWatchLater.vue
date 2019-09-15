<template lang='html'>
  <div id="watch-later-list">
    <ul style="list-style: none;">
      <watch-later-listitem v-for='filmToWatchLater in filmsToWatchLater' 
        :filmToWatchLater='filmToWatchLater'
        :key='filmToWatchLater.id'
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
#watch-later-list {
    color: lightsalmon;
    background-color: black;
}

</style>
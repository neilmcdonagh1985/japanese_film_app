<template lang='html'>
  <li>
      {{filmToWatchLater.title}}
  </li>
  
</template>

<script>
export default {
    name: 'watch-later-listitem',
    props: ['filmToWatchLater'] 


}
</script>

<style lang='css'>

</style>
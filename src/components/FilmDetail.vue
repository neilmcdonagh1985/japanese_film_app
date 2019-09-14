<template lang='html'>
  <div v-if='film'>
      <h2>{{film.title}}</h2>
      <p>{{film.release_date}}</p>
      <p>{{film.director}}</p>
      <p>{{film.description}}</p>
  </div>
  
</template>

<script>
export default {
    name: 'film-detail',
    props: ['film']

}
</script>

<style lang='css' scoped>

</style>
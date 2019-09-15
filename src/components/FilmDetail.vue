<template lang='html'>
<div id="film-details-container">
  <div id="film-details" v-if='film'>
      <h2>{{film.title}}</h2>
      <p>{{film.release_date}}</p>
      <p>{{film.director}}</p>
      <p>{{film.description}}</p>
  </div>
</div>
  
</template>

<script>
export default {
    name: 'film-detail',
    props: ['film']

}
</script>


<style lang='css' scoped>
#film-details-container {
    width: 50%;
}

</style>
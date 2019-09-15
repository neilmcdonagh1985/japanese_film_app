<template lang='html'>
<div id="film-details-container">
  <div id="film-details" v-if='film'>
      <h2>{{film.title}}</h2>
      <h3>{{film.release_date}}</h3>
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
    width: 25%;
    background-color: black;
    font-family: -apple-system, BlinkMacSystemFont, 
  'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 
  'Open Sans', 'Helvetica Neue', sans-serif;
  text-align: center;
}

#film-details {
    color: white;
}



</style>
<template>
  <div id="app">

  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  components: {
    
  },


  mounted(){
  axios.get('https://api.themoviedb.org/3/movie/popular?api_key=3c83c09e6615af6bfc5db9dc0a3760a3')
    .then(res => console.log(res.data.results)
    )
  }
}
</script>

<style lang="scss">

</style>

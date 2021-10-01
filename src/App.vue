<template>
  <div id="app" >
    <Header @search="dataSearch"/>
    <Main :bigData="filterArr"/>
  </div>
</template>

<script>
import axios from 'axios'
import Header from './components/header'
import Main from './components/main'

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },

  data(){
    return{
    dataFolder: [],
    dataSearched: '',
    }
  },

  methods:{

    dataSearch(x){
      this.dataSearched = x
    },

    log(x){
      console.log(x);
    }
  },

  computed: {
      filterArr(){
        if(this.dataSearched == '' ) return;
          return this.dataFolder.filter(el => el.title.toLowerCase().includes(this.dataSearched.toLowerCase()))
      },
    },


  mounted(){
  axios.get('https://api.themoviedb.org/3/movie/popular?api_key=3c83c09e6615af6bfc5db9dc0a3760a3')
    .then(res => this.dataFolder = [...res.data.results]
    )
  }
}
</script>

<style lang="scss">
@import './components/style/generalImportedFile.scss';



</style>

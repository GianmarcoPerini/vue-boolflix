<template>
  <div id="app">
    <Header :axMov="axiosMovies" :axSer="axiosSeries" />
    <Main :bigDataMovies="dataFolderMov" :bigDataSeries="dataFolderSer" :load="loading"/>
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
    dataFolderMov: [],
    dataFolderSer: [],
    apiKey: 'e99307154c6dfb0b4750f6603256716d',
    apiUrlMov: 'https://api.themoviedb.org/3/search/movie',
    apiUrlSer: 'https://api.themoviedb.org/3/search/tv',
    loading: false,
    id: [],
    }
  },

  methods:{

    axiosMovies(input){
      if(input.length > 1){
        axios.get(this.apiUrlMov, {
          params: {
            api_key: this.apiKey,
            query: input,
            page: this.count,
          }
        }).then(res => {
          this.dataFolderMov = [...res.data.results]
          this.loading = true
        }) 
      }
    },

    axiosSeries(input){
      if(input.length > 1){
        axios.get(this.apiUrlSer, {
          params: {
            api_key: this.apiKey,
            query: input,
            page: 1,
          }
        }).then(res => {
          this.dataFolderSer = [...res.data.results];
          this.loading = true
        }) 
      }
    },
  },
}

</script>

<style lang="scss">
@import './components/style/generalImportedFile.scss';

#app{
  background-color: #1f1c1d;
  height: 100vh;
  overflow-y: hidden;
}

</style>

<template>
  <div id="app">
    <Header :axMov="axiosMovies" :axSer="axiosSeries"/>
    <Main :bigDataMovies="filterArrMovies" :bigDataSeries="filterArrSeries" />
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
    dataSearchedMov: '',
    dataSearchedSer: '',
    }
  },

  methods:{

    axiosMovies(x){
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d', {
        params: {
          query: x,
        }
      }).then(res => {
        this.dataFolderMov = [...res.data.results]
        this.dataSearchedMov = x
        }) 
    },

    axiosSeries(y){
      axios.get('https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d', {
        params: {
          query: y,
        }
      }).then(res => {
        this.dataFolderSer = [...res.data.results]
        this.dataSearchedSer = y
        }) 
    },
  },

  computed: {
      filterArrMovies(){
          return this.dataFolderMov.filter(el => el.title.toLowerCase().includes(this.dataSearchedMov.toLowerCase()))
      },

      filterArrSeries(){
          return this.dataFolderSer.filter(el => el.name.toLowerCase().includes(this.dataSearchedSer.toLowerCase()))
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

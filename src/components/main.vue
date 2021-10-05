<template>
    <main>
        <div class="container mb-4">
            <h3 v-show="bigDataMovies.length != 0" class="text-white mb-3">Film</h3>
            <div class="card-wrapper row row-cols-xl-5 row-cols-md-3 row-cols-sm-2 row-cols-1">
                <template class="col" v-for="data in bigDataMovies">
                    <Card class="" v-if="data.poster_path != null" :key="data.id" :movID="data.id" :poster="data.poster_path" :title="data.title" :orTitle="data.original_title" :language="data.original_language" :vote="data.vote_average"/>
                </template>
            </div>
        </div>
        
        <div class="container mb-5 pt-5">
            <h3 v-show="bigDataSeries.length != 0" class="text-white mb-3">Serie TV</h3>
            <div class="card-wrapper row row-cols-xl-5 row-cols-md-3 row-cols-sm-2 row-cols-1">
                <template class="col" v-for="data in bigDataSeries" >
                    <Card class="" v-if="data.poster_path != null" :key="data.id" :prova="load" :movID="data.id" :poster="data.poster_path" :name="data.name" :orName="data.original_name" :language="data.original_language" :vote="data.vote_average"/>
                </template>
            </div>
        </div>
    </main>
</template>

<script>
import Card from './card'


export default {
    name: 'Main',
    props: {
        bigDataMovies: Array,
        bigDataSeries: Array,
        load: Boolean
    },
    components: {
        Card,
    },
    methods: {
        log(x){
            console.log(x);
        }
    },
}
</script>

<style lang="scss" >
@import './style/generalImportedFile';

main{
    
    height: calc(100vh - 130px);
    overflow-y: scroll;
}
</style>
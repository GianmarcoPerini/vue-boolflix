<template>
    <main>
            
            <div class="container mb-4">
                <h3 class="text-white mt-5 mb-3" v-show=" bigDataMovies.length > 0 ">Film</h3>
                <div class="card-wrapper row row-cols-xl-5 row-cols-md-3 row-cols-sm-2 g-1">
                    <div v-show=" data.poster_path != null " class="col" v-for="data in bigDataMovies" :key="data.id">
                        <div  class="single-card position-relative">
                            <div class="cover position-absolute">
                                <img :src="'https://image.tmdb.org/t/p/original' + data.poster_path" :alt="data.poster_path">
                            </div>
                            <div class="info">
                                <h4 class="fw-bold mb-3 text-center">{{data.title}}</h4>
                                <p class="mb-2 ps-2">Titolo originale: <span class="min">{{data.original_title}}</span></p>
                                <p class="center mb-3 ps-2">Voto: <Rating class="ms-3" :vote="data.vote_average"/></p>
                                <p class="mb-2 ps-2" v-if="( data.original_language == 'it' )">Lingua: 
                                    <img class="ms-2" src="../assets/Flag_of_Italy.svg" alt="">
                                </p>
                                <p class="mb-1 ps-2" v-else-if="(data.original_language == 'en')">Lingua: 
                                    <img class="ms-2" src="../assets/Flag_of_the_United_Kingdom.svg" alt="">
                                </p>
                                <p class="mb-1 ps-2" v-else>Lingua: <span class="min">{{data.original_language}}</span></p>
                            </div>
                        </div>
                        
                        
                    </div>
                </div>
            </div>

            <div class="container">
                <h3 class="text-white mt-5 mb-3" v-show=" bigDataSeries.length > 0 ">Serie tv</h3>
                <div class="card-wrapper row row-cols-xl-5 row-cols-md-3 row-cols-sm-2 row-cols-1 g-1">
                    <div v-show="data.poster_path != null" class="col" v-for="data in bigDataSeries" :key="data.id">
                        <div class="single-card position-relative">
                            <div class="cover position-absolute">
                                <img :src="'https://image.tmdb.org/t/p/original' + data.poster_path" :alt="data.poster_path">
                            </div>
                            <div class="info">
                                <h4 class="fw-bold mb-2 text-center">{{data.name}}</h4>
                                <p class="mb-2 ps-2">Titolo originale: <span class="min">{{data.original_name}}</span></p>
                                <p class="center mb-3 ps-2">Voto <Rating class="ms-3" :vote="data.vote_average"/></p>
                                <p class="mb-2 ps-2" v-if="( data.original_language == 'it' )">Lingua: 
                                    <img class="ms-2" src="../assets/Flag_of_Italy.svg" alt="">
                                </p>
                                <p class="mb-1 ps-2" v-else-if="(data.original_language == 'en')">Lingua: 
                                    <img class="ms-2" src="../assets/Flag_of_the_United_Kingdom.svg" alt="">
                                </p>
                                <p class="mb-1 ps-2" v-else>Lingua: <span class="min">{{data.original_language}}</span></p>
                            </div>
                        </div>
                        
                    </div>
                </div>
            </div>
            
                


    </main>
</template>

<script>
import Rating from './rating'


export default {
    name: 'Main',
    props: {
        bigDataMovies: Array,
        bigDataSeries: Array,
    },
    components: {
        Rating,
    },

    data(){
        return{

        }
    },

}
</script>

<style lang="scss" scoped>
@import './style/generalImportedFile';

main{
    
    height: calc(100vh - 130px);
    overflow-y: scroll;

    .single-card{
        aspect-ratio: 1/1.3;
        background-color: #1f1c1d;
        padding-top: 20px;
        z-index: 0;
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
        

        &:hover .info{
            z-index: 2;
            opacity: 1;
        }

        &:hover .cover{
        opacity: .3;
        z-index: -1;
        }

        .cover{
            inset: 0 0 0 0;
            transition: opacity 200ms;


            
            img{
                width: 100%;
                height: 100%;
                object-fit: fill;
            }
            
        }

        p{
            color: white;
            font-weight: bold;
        }

        h4{
            color: white;
        }
    }

    .info img{
        height: 20px;
    }

    .min{
        font-weight: normal;
    }
    .center{
        display: flex;
        align-items: flex-end;
    }

    
}


</style>
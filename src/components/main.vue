<template>
    <main class="bg-secondary">
            <div class="container mt-4 mb-4">
                <div class="card-wrapper row row-cols-5 g-3">
                    <div class="col" v-for="(data, i) in bigDataMovies" :key="i">
                        <div class="single-card position-relative">
                            <div class="cover position-absolute">
                                <img src="https://via.placeholder.com/400x400" alt="">
                            </div>
                            <div class="info">
                                <h4 class="text-white mb-4 text-center">Titolo: {{data.title}}</h4>
                                <p class="m-0 ps-2">Titolo originale: {{data.original_title}}</p>
                                <p class="m-0 ps-2">Voto {{data.vote_average}}</p>
                                <p class="m-0 ps-2" v-if="( data.original_language == 'it' )">Lingua: 
                                    <img class="w-25" src="../assets/Flag_of_Italy.svg" alt="">
                                </p>
                                <p v-else-if="(data.original_language == 'en')"> Lingua: 
                                    <img class="w-25" src="../assets/Flag_of_the_United_Kingdom.svg" alt="">
                                </p>
                            </div>
                        </div>
                        
                    </div>
                </div>
            </div>

            <div class="container mt-4 mb-4">
                <div class="card-wrapper row row-cols-5 g-3">
                    <div class="col" v-for="(data, i) in bigDataSeries" :key="i">
                        <div class="single-card position-relative">
                            <div class="cover position-absolute">
                                <img src="https://via.placeholder.com/400x400" alt="">
                            </div>
                            <div class="info">
                                <h4 class="text-white mb-4 text-center">Titolo: {{data.name}}</h4>
                                <p class="m-0 ps-2">Titolo originale: {{data.original_name}}</p>
                                <p class="m-0 ps-2">Voto {{data.vote_count}}</p>
                                <p class="m-0 ps-2" v-if="( data.original_language == 'it' )">Lingua: 
                                    <img class="w-25" src="../assets/Flag_of_Italy.svg" alt="">
                                </p>
                                <p v-else-if="(data.original_language == 'en')"> Lingua: 
                                    <img class="w-25" src="../assets/Flag_of_the_United_Kingdom.svg" alt="">
                                </p>
                            </div>
                        </div>
                        
                    </div>
                </div>
            </div>
            
                


    </main>
</template>

<script>
export default {
    name: 'Main',
    props: ['bigDataMovies', 'bigDataSeries'],

}
</script>

<style lang="scss" scoped>
@import './style/generalImportedFile';

main{
    height: calc(100vh - 100px);
    overflow-y: scroll;

    .single-card{
        aspect-ratio: 1/1.5;
        background-color: aqua;
        padding-top: 20px;

        &:hover .cover{
        transform: scale(0,1);
        opacity: 0;
        transition-delay: opacity 200ms;
    }

        .cover{
            inset: 0 0 0 0;
            background-color: red;
            transform: scale(1,1);
            transform-origin: left;
            opacity: 1;
            transition: transform 500ms ease-in-out, opacity 200ms ease-in-out 100ms;

            
            img{
                width: 100%;
                height: 100%;
            }
            
        }

        p{
            color: green;
        }
    }

    
}


</style>
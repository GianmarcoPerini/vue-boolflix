<template>
    <main class="bg-secondary">
            <div class="container mt-4 mb-4">
                <div class="card-wrapper row row-cols-5 g-3">
                    <div class="col" v-for="(data, i) in bigData" :key="i">
                        <div class="single-card">
                            <div class="img-box mb-4">
                                <img src="https://via.placeholder.com/400x400" alt="">
                            </div>
                            <div class="info text-center">
                                <h4 class="text-white mb-4">{{data.title}}</h4>
                                <p class="m-0">{{data.original_title}}</p>
                                <p class="m-0">{{data.vote_average}}</p>
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
    props: ['bigData'],

}
</script>

<style lang="scss" scoped>
@import './style/generalImportedFile';

main{
    height: calc(100vh - 100px);
    overflow-y: scroll;

    .single-card{
        // width: 100%;
        aspect-ratio: 1/1.5;
        background-color: aqua;
        padding-top: 20px;

        p{
            color: green;
        }

        .img-box{
            width: 80%;
            margin: 0 auto;
            aspect-ratio: 1/1;

            img{
                width: 100%;
                height: 100%;
                object-fit: fill;
            }
        }
    }
}


</style>
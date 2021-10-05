<template>
    <div class="single-card position-relative ">
        <div class="cover position-absolute">
            <img :src="'https://image.tmdb.org/t/p/original' + poster" :alt="poster">
        </div>
        <div class="info">
            <h4 class="fw-bold mb-3 text-center">{{title ? title : name}}</h4>
            <p class="mb-2 ps-2">Titolo originale: <span class="min">{{orTitle ? orTitle : orName}}</span></p>
            <p class="center mb-3 ps-2">Voto: <Rating class="ms-3" :vote="vote"/></p>
            <p class="mb-2 ps-2" v-if="( language == 'it' )">Lingua: 
                <img class="ms-2" src="../assets/Flag_of_Italy.svg" alt="">
            </p>
            <p class="mb-1 ps-2" v-else-if="(language == 'en')">Lingua: 
                <img class="ms-2" src="../assets/Flag_of_the_United_Kingdom.svg" alt="">
            </p>
            <p class="mb-1 ps-2" v-else>Lingua: <span class="min">{{language}}</span></p>
            <div class="text-white" v-for="(el,i) in catsNameFn(movID)" :key="i">{{el}}</div>
        </div>
    </div>
    
</template>

<script>
import axios from 'axios'
import Rating from './rating.vue'
export default {    
    name: 'Card',
    props:{
        movID: Number,
        poster: String,
        title: String,
        orTitle: String,
        name: String,
        orName: String,
        language: String,
        vote: Number,
    },
    components:{
        Rating,
    },
    data(){
        return{
        id:'',
        apiUrl: 'e99307154c6dfb0b4750f6603256716d',
        cast: [],
        
        }
    },

    mounted() {
        axios.get(`https://api.themoviedb.org/3/movie/${this.id}/credits?`, {
            params: {
                api_key: this.apiUrl
            }
        }).then(res => {
            this.cast = [...res.data.cast]
        })
        .catch((error) => {
            console.log('errore= ' + error);
        })
    },

    methods: {

        catsNameFn(id){
            let catsName = [];
            this.id = id;
            this.cast.forEach(el => {
                if(catsName.length < 5){
                    catsName.push(el.name)
                } 
            })
            return catsName
        }
    }
}
</script>

<style lang="scss" scoped>

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

</style>
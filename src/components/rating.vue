<template>
    
        <star-rating v-model="rating" :read-only="true" :showRating="false" :item-size="15"></star-rating>
    
</template>

<script type="text/javascript">   
import {StarRating} from 'vue-rate-it';


export default{
    components: {
        StarRating,
    },
    props: {
        vote: Number,
    },

    data(){
        return {

            rating: 0,
    }
},

    mounted() {
        
            this.rating = Math.round(this.vote / 2)
        
    },
}
</script>

<style lang="scss" >



</style>
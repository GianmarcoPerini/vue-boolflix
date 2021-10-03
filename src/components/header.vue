<template>
    <header class="container" >
        
            <div class="row justify-content-between align-items-center">
                <div class="logo col-md-6 col-12">
                    <img src="../assets/peraflix.png" alt="">
                </div>

                <div class="input-box col-md-6 col-12">
                    <input class="me-4" type="text" v-model.trim=" myInput " @keyup.enter=" axMov(myInput), axSer(myInput) ">
                    <button @click=" axMov(myInput), axSer(myInput) "> Ricerca </button>
                </div>
            </div>
        
        
    </header>
</template>

<script>
export default {
    name:'Header',
    props:{
        axMov: Function,
        axSer: Function,
    },

    data(){
        return{
            myInput: '',
        }
    },
}
</script>

<style lang="scss" scoped>
@import './style/generalImportedFile';

    .input-box{
        text-align: end;
    }

    @media only screen and (max-width: 768px){
        .input-box{
            text-align: start;
        }
    }


</style>
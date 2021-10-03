<template>
    <header class="container" >
            <div class="row justify-content-between align-items-center">
                <div class="logo col-md-6 col-12">
                    <img src="../assets/peraflix.png" alt="">
                </div>

                <div class="input-box col-md-6 col-12">
                    <form @submit.prevent>
                        <input class="me-4" type="search" v-model.trim=" myInput " @keyup.enter=" axMov(myInput), axSer(myInput), reset()">
                        <button type="reset" @click=" axMov(myInput), axSer(myInput) "> Ricerca </button>
                    </form>
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

    methods:{
        reset(){
            if(this.myInput != '') this.myInput = '';
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
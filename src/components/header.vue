<template>
    <header class="d-flex justify-content-between align-items-center ps-2 pe-5">
        <div class="logo">
            <img src="../assets/peraflix.png" alt="">
        </div>

            <div class="input-box">
                <input class="me-4" type="text" v-model.trim="myInput">
                <button @click=" axMov(myInput), axSer(myInput) "> Ricerca </button>
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

    header{
        height: 100px;
        background-color: blue;
    }


</style>
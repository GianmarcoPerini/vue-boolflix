<template>
    <main class="bg-secondary">
        <div v-for="(data, i) in bigData" :key="i">{{data.title}}</div>
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
    }


</style>
<template>
<div>
<div v-if="isLoggedIn" class="image-container">
   <img v-for='image in allImages' v-bind:src="image.link" :key="image"/>
</div>
<h2 v-else>LogIn to get started!</h2>
</div>
</template>
<script>
import {mapActions, mapGetters} from 'vuex';
export default {
    name: 'ImageList',
    computed: mapGetters(['allImages', 'isLoggedIn']),
    methods: mapActions(['fetchImages']),
    created(){
        this.fetchImages();
    }
};
</script>
<style scoped>
    .image-container{
        column-count: 3;
        column-gap: 0;

    }
    img{
        max-width: 100%;
        padding: 5px;
    }
</style>
<script>
import axios from 'axios';

export default {
    name: 'Appmain',
    data() {
        return {
           photos: [],
        }

    },
    methods: {

        loadPhotos() {

            axios.get(`http://localhost:8080/api/v1/photos`).then(resp => {

                this.photos = resp.data;
                console.log(this.photos);

            })

        }

    },
    created() {

        this.loadPhotos();

    },
    mounted() {
        
    }
}


</script>

<template>

    <div class="col-xs-eight col-xs-offset-two ">   
        <div class="flex-row-spc-btwn-start">
            <div v-for="photo in photos" class="card">
                <h2>{{ photo.title }}</h2>
                <h3>{{ photo.description }}</h3>
                <img :src="photo.url" :alt="photo.title">
                <span v-for="category in photo.categories">{{ category.name }}</span>
            </div>
        </div>
    </div>

</template>

<style scoped>

    img {

        width: 100%;

    }

</style>
<template lang="html">
    <h1>{{album.title}}</h1>
</template>

<script>
import axios from 'axios';
import router from 'vue-router';
import env from '../../config/env';
export default {
    name: 'AlbumIndvPage',
    data(){
        return{
            album: {},
            photos: []
        }
    },
    created(){
        //console.log(this.$route);
        //let albumId = this.$route.params.id;
        //console.log(albumId);
        axios.get(`${env.enpoint}/albums/${this.$route.params.id}`)
        .then(albumResponse=>{
            this.album = albumResponse.data;
        })
    }
}
</script>
<style lang="css">

</style>
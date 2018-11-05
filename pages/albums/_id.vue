<template lang="html">
<div class="container">
    <header>
        <h1 class="title">{{album.title}}</h1>
        <nuxt-link to="/" class="button is-link">Regresar</nuxt-link>
    </header>
   <div class="columns is-multiline">
       <div class="column is-one-quarter" v-for="photo in photos" :key="photo.id">
           <img :src="photo.url " :alt="photo.tile" />
       </div>
   </div>

</div>
</template>

<script>
import axios from "axios";
import router from "vue-router";
import env from "../../config/env";
export default {
  name: "AlbumIndvPage",
  data() {
    return {
      album: {},
      photos: []
    };
  },
  /*created() {
    //console.log(this.$route);
    //let albumId = this.$route.params.id;
    //console.log(albumId);
    axios
      .get(`${env.endpoint}/albums/${this.$route.params.id}`)
      .then(albumResponse => {
        this.album = albumResponse.data;
      });
    axios
      .get(`${env.endpoint}/albums/${this.$route.params.id}/photos`)
      .then(photosResponse => {
        this.photos = photosResponse.data;
      });*/
      created: async function () {
        let albumResponse = await axios.get(`${env.endpoint}/albums/${this.$route.params.id}`);
        this.album = albumResponse.data;
        let photoResponse = await axios.get(`${env.endpoint}/albums/${this.$route.params.id}/photos`);
        this.photos = photoResponse.data;

      }

};
</script>
<style scoped>
.container {
  text-align: center;
}

</style>

<template lang="html">
    <div class="column is-one-quarter">
        <div class="box">
        <h3>{{album.title}}</h3>
        <a href="#" class="button is-primary">Ver Álbum</a>
        </div>
    </div>
</template>

<script>
export default {
  name: "AlbumCard",
  props: {
    album: Object
  }
};
</script>


<style lang="css">
.box{
    paddiing:1em;
}
h3{
    min-height: 5em;
}
</style>

<template>
    <div class="pelicula">
      <div class="col-8 col-sm-8">
          <strong><img v-b-tooltip.hover :title="infopelicula.titulo"  class="img-fluid shadow" :src="'https://image.tmdb.org/t/p/w500/'+ infopelicula.poster"/></strong>
      </div>
    </div>
</template>

<script>
export default {
  name: 'componente-pelicula',
  props: {
    infopelicula: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.pelicula{
  background: black;
}
.img-fluid{
  height: 80vh;
  border-radius: 15px;
  margin-top:15px;
  margin-left:30%;
  width:80%;
}

</style>

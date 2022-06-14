<template>
<div id="app">
 <b-row >
    <b-col md="6" v-for="(item,index) of infopeliculas" :key="index">
      <Pelicula  :infopelicula="item"/> 
    </b-col>
  </b-row>
</div>
</template>

<script>
import Pelicula from './pelicula.vue'
export default {
  name: 'HelloWorld',
  components: {
    Pelicula
  },
  data(){
    return{
      infopeliculas:{}
    }
  },
  created (){
    this.CargarPeliculas()
  },
  methods:{
     async CargarPeliculas(){ //funcion para obtener peliculas 

    try{ //se utiliza para funciones asincronas
        const respuesta = await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=afa20cf97d3ba149a0670b053c7d908e&language=es-MX&page=2`); //funcion para conectarse a la API
        //se crea la variable respuesta para mostrar el resultado de la peticion

        const peliculas=await respuesta.json()
        for(const pelicula in peliculas.results){
          this.$set(this.infopeliculas,pelicula,{titulo:peliculas.results[pelicula].title, poster:peliculas.results[pelicula].poster_path})
        }

    }catch(error){//En caso de que haya un error con la petición
        console.log(error); //muestra error en consola
        
    }

}
  }
}
</script>
<style scoped>
.col-md-6{
  padding:0;
}
</style>
<!-- Add "scoped" attribute to limit CSS to this component only -->

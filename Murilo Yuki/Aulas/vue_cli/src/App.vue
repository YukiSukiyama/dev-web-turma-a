<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>Meu App Vue</h1>
    <p class="subtitulo">Meu subtitulo</p>
    <br />
    <home-component />
    <hr />
    <br />
    <usuario-component />
    <hr />
    <br />
    <estilo-component/>
  </div>
</template>

<script>
import HomeComponent from './components/HomeComponent.vue';
import UsuarioComponent from './components/UsuarioComponent.vue';
import EstiloComponent from './components/EstiloComponent.vue';



export default {
  name: 'App',
  components: {
    HomeComponent,
    UsuarioComponent,
    EstiloComponent,
  },
created(){
  console.log("created")
  },
mounted(){
  console.log("mouted")
  },
updated(){
  console.log("updated")
  },
errorCaptured(){
  console.log("erro")
  },
};


</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  color: darkblue;
  text-align: center;
}
.subtitulo{
  color: chocolate;
  font-family: "Gill Sans";
  text-align: center;
}
</style>

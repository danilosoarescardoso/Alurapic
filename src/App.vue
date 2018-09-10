<template>
  <div>
    <h1>{{ titulo }}</h1>
    <li v-for="foto of fotos" :key="foto">
      <img :src="foto.url" :alt="foto.titulo">
    </li>
  </div>
</template>

<script>
export default {
  data(){
    return{
      titulo: 'Alurapic', 
      fotos:[]
    }
  },

  created(){
    alert('Criei o componente');
  }
}
</script>

<style>

</style>

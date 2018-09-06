<template>
  <div>
    <h1>{{ titulo }}</h1>
    <li v-for="foto of fotos">
      <img :src="foto.url" :alt="foto.titulo">
    </li>
  </div>
</template>

<script>
export default {
  data(){
    return{
      titulo: 'Alurapic', 
      fotos:[
        {
        url: 'https://www.torcedores.com/content/uploads/2017/11/palmeiras1-1.jpg',
        titulo: 'cachorro'
      }, 
      {
        url: 'https://www.torcedores.com/content/uploads/2017/11/palmeiras1-1.jpg',
        titulo: 'cachorro'
      }
      ]
    }
  }
}
</script>

<style>

</style>

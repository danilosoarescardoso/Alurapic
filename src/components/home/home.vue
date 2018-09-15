<template>
  <div>
    <h1 class="centralizado">{{ titulo }}</h1>
    <input type="search" class="filtro" @input="filtro = $event.target.value" placeholder="filtre por parte do título">
    {{ filtro }}
    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="foto of fotosComFiltro" :key="foto">

        <meu-painel :titulo="foto.titulo">
          <imagem-responsiva :url="foto.url" :titulo="foto.titulo"></imagem-responsiva>
          <meu-botao tipo="button" rotulo="Remover" @click.native="remove(foto)"/>
        </meu-painel>
      </li>
    </ul>
  </div>
</template>

<script>
import Painel from '../shared/painel/Painel.vue';
import imagemResponsiva from '../shared/imagem-responsiva/imagemResponsiva.vue';
import Botao from '../shared/botao/Botao.vue';

export default {

  components:{
    'meu-painel': Painel,
    'imagem-responsiva': imagemResponsiva,
    'meu-botao' : Botao
  },

  data(){
    return{
      titulo: 'Alurapic', 
      fotos:[],
      filtro: ''
    }
  },

  computed: {

    fotosComFiltro(){
      if (this.filtro){
        /* filtrar */
        let exp = new RegExp(this.filtro.trim(), 'i');
        return this.fotos.filter(foto => exp.test(foto.titulo));
      } else{
        return this.fotos;
      }
    }

  },

  methods: {
    remove(foto){
      if (confirm('Confirma a Operação?')){
        alert('Remover a foto ' + foto.titulo);
      }
    }
  },

  created(){
    let promise = this.$http.get('http://localhost:3000/v1/fotos')
      .then(res => res.json())
      .then(fotos => this.fotos = fotos, err => console.log(err));

  }
}
</script>

<style scoped>



.centralizado{
  text-align: center;
  }

  .lista-fotos {
    list-style: none;
  }

  .lista-fotos .lista-fotos-item {
    display: inline-block;
  }
  

  .filtro{
    display: block;
    width: 100%;
  }

</style>

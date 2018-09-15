<template>
  <div class="corpo">

    <nav>
      <ul>
        <li v-for="route in routes" :key="route.path"> 
          <router-link :to="route.path ? route.path : '/' ">{{ routes.titulo }}</router-link>
        </li>
      </ul>
    </nav>
   
    <router-view></router-view>
  </div>
</template>

<script>

import { routes } from './routes';

export default {  

  data(){
    return{
      routes
    }
  }
}
</script>

<style scoped>

.corpo{
  font-family: Helvetica, sans-serif;
  width: 96%;
  margin: 0 auto;
}

</style>

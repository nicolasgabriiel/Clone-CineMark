<template>
  <div class="principal-container">
  <div>
    <CarrosselDeImagens/>
  </div>
  <button @click="getData">Obter dados da API</button>
  </div>
</template>

<script lang="ts">
import CarrosselDeImagens from '@/components/CarrosselDeImagens.vue';
import { defineComponent} from 'vue';
import axios from 'axios';


export default defineComponent({
  name: 'App',
  async mounted(){
      try {
        const response = await axios.get('https://api.themoviedb.org/3/movie/76341?api_key=ea50df2fafdaa8c0f5c42dfbb1bd82f9&language=pt-BR');
        console.log(response.data);
      } catch (error) {
        console.error(error);
      }
    
  },
  components:{
    CarrosselDeImagens
  }
    
});

</script>

<style scoped>
.principal-container{
  width: 100%;
  min-height: 100vh;
  height: auto;
  background-color: black;
}
</style>
<template>
    <div class="container-filmes" v-for="(Filme, index) in Filmes" :key="Filme"  >
        <div class="imagem" :style="{ backgroundImage: 'url(' + Filme + ')' }"></div>
  <h1 class="nome">{{ Nomes[index] }}</h1>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import axios from 'axios';
export default defineComponent({
    name: 'Filmes-em-cartaz',
    async mounted(){
      try { 
        const listaIdsFilmes = [502356,594767,603692,758323,804150,493529,1008005]
        for(let i = 0; i < 7; i++){
        const response = await axios.get(`https://api.themoviedb.org/3/movie/${listaIdsFilmes[i]}?api_key=${this.key}`);
        this.urlFilmes[i] = response.data.poster_path;
        this.Filmes[i] = this.buscadorDeImagem + this.urlFilmes[i];
        this.Nomes[i] = response.data.original_title
      }
      console.log(this.Filmes)
    } catch (error) {
        console.error(error);
      }
  },
  data(){
    return{
      buscadorDeImagem: 'http://image.tmdb.org/t/p/original',
      key: 'ea50df2fafdaa8c0f5c42dfbb1bd82f9',
      urlFilmes: [''],
      Filmes: [''],
      Nomes: ['']
    }
  },
})
</script>

<style scoped>
.container-filmes{

}
.imagem{
    height: 30vh;
    width: 46.3%;
    background-size: contain;
}
.nome{
    font-size: 20px;
    color: white
}
</style>
<template>
  <div class="container-carrossel" :style="{ backgroundImage: 'url(' + FilmeNaTela + ')' }">
    <div class="controles-carrossel">
      <div class="container-botão">
        <button>comprar ingresso</button>
      </div> <!--Container Botoes -->
      <div class="container-botoes">
        <ul class="lista-botoes"> 
          <li :class="{ 'filme-mostrado': botaoAtivo[0], }"><button @click="MudarFilme(0)"></button></li>
          <li :class="{ 'filme-mostrado': botaoAtivo[1], }"><button @click="MudarFilme(1)"></button></li>
          <li :class="{ 'filme-mostrado': botaoAtivo[2], }"><button @click="MudarFilme(2)"></button></li>
          <li :class="{ 'filme-mostrado': botaoAtivo[3], }"><button @click="MudarFilme(3)"></button></li>
          <li :class="{ 'filme-mostrado': botaoAtivo[4], }"><button @click="MudarFilme(4)"></button></li>
          <li :class="{ 'filme-mostrado': botaoAtivo[5], }"><button @click="MudarFilme(5)"></button></li>
          <li :class="{ 'filme-mostrado': botaoAtivo[6], }"><button @click="MudarFilme(6)"></button></li>
        </ul> <!-- Lista Botões -->
       </div> <!--Container Botoes -->
     </div> <!--Controles Carrossel -->
   </div> <!--Container Carrossel -->
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import axios from 'axios';

export default defineComponent({
  name: 'Carrossel-de-Imagens',
  async mounted(){
      try { 
        const listaIdsFilmes = [502356,594767,603692,758323,804150,493529,1008005]
        for(let i = 0; i < 7; i++){
        const response = await axios.get(`https://api.themoviedb.org/3/movie/${listaIdsFilmes[i]}?api_key=${this.key}`);
        this.urlFilmes[i] = response.data.poster_path;
        this.Filmes[i] = this.buscadorDeImagem + this.urlFilmes[i];
      }
      this.FilmeNaTela = this.Filmes[0]
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
      FilmeNaTela: '',
      botaoAtivo:[true,false,false,false,false,false,false]
    }
  },
  methods:{
    MudarFilme(indice:number){
      this.FilmeNaTela = this.Filmes[indice]
      this.botaoAtivo = [false,false,false,false,false,false,false]
      this.botaoAtivo[indice] = true
    }
  }
});
</script>

<style scoped>
.container-carrossel {
  font-family: 'Raleway', sans-serif;
  width: 100%;
  height: 35vh;
  background-size: 60%;
  background-position: center;
  background-repeat: no-repeat;
  display: flex;
  justify-content: center;
  align-items: flex-end;
}
.container-botão button{
  background-color: red;
  border: none;
  font-size: 0.6em;
  font-weight: 800;
  text-transform: uppercase;
  padding: 7px 5px;
  border-radius: 2px;
  color: white;
  cursor: pointer;
  transition: .5s;
}
.container-botão button:hover{
  scale: 1.03;
}
.container-botoes{
  display: flex;
  justify-content: center;
}
.lista-botoes{
  display: flex;
  flex-direction: row;
  padding: 0;
}
li{
  list-style-type: none;
  width: 8px;
  height: 8px;
  border-radius: 4px;
  background-color: #cccccc;
  margin: 3px;
}
li:hover{
  background-color: #b9b7b7dd;
}
li button{
  width: 100%;
  height: 100%;
  display: block;
  background-color: transparent;
  border: none;
  color: inherit;
  text-decoration: none;
  font-size: inherit;
  font-family: inherit;
  padding: 0;
  margin: 0;
  cursor: pointer;
}
.filme-mostrado{
  background-color: red !important; 
}

</style>

<template>
  <div class="container-carrossel" :style="{ backgroundImage: 'url(' + Filme1 + ')' }">
    <div class="controles-carrossel">
      <div class="container-botão">
        <button>comprar ingresso</button>
      </div>
      <div class="container-botoes">
        <ul class="lista-botoes"> 
          <li><button></button></li>
          <li><button></button></li>
          <li><button></button></li>
          <li><button></button></li>
          <li><button></button></li>
          <li><button></button></li>
          <li><button></button></li>
        </ul>
      </div>
    </div>
  </div>
  <img src=""/>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import axios from 'axios';

export default defineComponent({
  name: 'Carrossel-de-Imagens',
  async mounted(){
      try { 
        const response = await axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.key}&query=O+Exorcista+Do+Papa`);
        console.log(response.data.results[0].backdrop_path);
        this.urlFilme1 = response.data.results[0].backdrop_path;
        this.Filme1 = this.buscadorDeImagem + this.urlFilme1
        console.log(this.Filme1)
      } catch (error) {
        console.error(error);

      }
    
  },
  data(){
    return{
      imageUrl:  'http://image.tmdb.org/t/p/original/tH64gzAHDFg7EFcgfkkZyHdGM5P.jpg',
      buscadorDeImagem: 'http://image.tmdb.org/t/p/original',
      key: 'ea50df2fafdaa8c0f5c42dfbb1bd82f9',
      urlFilme1: '',
      Filme1:''
    }
  }
});
</script>

<style scoped>
.container-carrossel {
  width: 100%;
  height: 35vh;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
.controles-carrossel{
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 55% ;

}
.lista-botoes{
  display: flex ;
}
.container-botão button{
  background-color: red;
  border: none;
  font-size: 0.6em;
  font-weight: bold;
  text-transform: uppercase;
  padding: 7px 5px;
  border-radius: 3px;
  color: white;
}
.container-botoes{
  display: flex;
  justify-content: space-between;
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
  cursor: pointer;
}
li button{
  width: 100%;
  height: 100%;
  background-color: transparent;
  border: none;
  color: inherit;
  text-decoration: none;
  font-size: inherit;
  font-family: inherit;
  padding: 0;
  margin: 0;
}

</style>

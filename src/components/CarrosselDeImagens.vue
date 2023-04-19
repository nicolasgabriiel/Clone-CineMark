<template>
  <div class="container-carrossel">
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
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Carrossel-de-Imagens',
});
</script>

<style scoped>
.container-carrossel {
  width: 100%;
  height: 35vh;
  background-color: aliceblue;
  
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

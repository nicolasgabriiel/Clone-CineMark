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
</style>

<template>
    <h1>Filmes em Cartaz</h1>
    <div class="box">
        <div class="container-filmes" v-for=" filme in FilmesFiltrados" :key="filme.id" :class="filme.identificador">
            <div class="imagem" :style="{ backgroundImage: 'url(' + filme.url + ')' }"></div>
            <h2 class="nome">{{ filme.nome }}</h2>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import axios from 'axios';

interface Filme {
    id: number;
    nome: string;
    url: string;
    identificador: number;
}


export default defineComponent({
    name: 'Filmes-em-cartaz',
    async mounted() {
        try {
            const listaIdsFilmes = [502356, 594767, 603692, 758323, 804150, 493529, 1008005]
            for (let i = 0; i < 7; i++) {
                const response = await axios.get(`https://api.themoviedb.org/3/movie/${listaIdsFilmes[i]}?api_key=${this.key}`);
                this.filmes[i] = {
                    id: response.data.id,
                    nome: response.data.original_title,
                    url: this.buscadorDeImagem + response.data.poster_path,
                    identificador: i
                };
            }
            console.log(this.filmes)
        } catch (error) {
            console.error(error);
        }
    },
    data() {
        return {
            buscadorDeImagem: 'http://image.tmdb.org/t/p/original',
            key: 'ea50df2fafdaa8c0f5c42dfbb1bd82f9',
            filmes: [] as { id: number, nome: string, url: string, identificador: number }[],
            mostrar: [true, false, false, false, false, false, false],
        }
    },
    computed: {
        FilmesFiltrados(): Filme[] {
            return this.filmes.filter((filme: Filme, index: number) => this.mostrar[index]);
        },

    }
})
</script>

<style scoped>
.box {
    display: flex;
    flex-direction: row;
}

.container-filmes {
    display: flex;
    flex-direction: column;
}

.imagem {
    height: 30vh;
    width: 46.3%;
    background-size: contain;
}

.nome {
    font-size: 20px;
    color: black
}

.hide {
    display: none !important;
}
</style>
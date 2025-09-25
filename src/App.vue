<script lang="ts">
import aFera from '@/assets/imagens-filme/filme-a-fera.jpg';
import alvoSecreto from '@/assets/imagens-filme/filme-alvo-secreto.jpg';
import capitaoAmerica from '@/assets/imagens-filme/filme-capitao-america.jpeg';
import comoEuEraAntesDVoce from '@/assets/imagens-filme/filme-como-eu-era-antes-de-voce.jpg';
import pecadores from '@/assets/imagens-filme/filme-pecadores.jpg';
import FilmeItem from './components/FilmeItem.vue';

export default {
    data() {
        return {

            favorito: 0,

            listaDeFilmes: [
                {
                    nome: "A Fera",
                    descricao: "O Dr. Nate Samuels, depois de perder a esposa, viaja com suas filhas para uma reserva na África do Sul — um lugar que tinha significado pra ele. Mas a viagem vira pesadelo quando eles são perseguidos por um leão selvagem.",
                    ano: "2022",
                    imagem: aFera
                },
                {
                    nome: "Alvo Secreto",
                    descricao: "Um assassino de aluguel da CIA descobre que sua divisão foi encerrada há muito tempo. Ele parte para descobrir quem realmente vinha lhe dando ordens.",
                    ano: "2024",
                    imagem: alvoSecreto
                },
                {
                    nome: "Capitão America",
                    descricao: "Sam Wilson assume oficialmente o papel de Capitão América após Steve Rogers. Ele se vê envolvido em uma conspiração internacional quando o presidente Thaddeus Ross manda investigar itens confidenciais roubados; ele precisa impedir que a trama cause um caos global.",
                    ano: "2025",
                    imagem: capitaoAmerica
                },
                {
                    nome: "Como eu era antes de você",
                    descricao: "Louisa “Lou” Clark, uma jovem de origem modesta, aceita cuidar de Will Traynor, um homem rico que ficou tetraplégico após um acidente. Ela tenta mostrar a ele que ainda há motivos para viver, e entre os dois nasce uma ligação profunda.",
                    ano: "2016",
                    imagem: comoEuEraAntesDVoce
                },
                {
                    nome: "Pecadores",
                    descricao: "Dois irmãos gêmeos retornam à cidade natal para reconstruir suas vidas, mas passado e traumas revivem quando uma força sobrenatural ameaça sua comunidade. É um thriller com elementos sobrenaturais, ambientado no Delta do Mississippi.",
                    ano: "2025",
                    imagem: pecadores
                }
            ],
            mensagem: ''
        }
    },

    methods: {
        adicionadoAoFavoritos(filme: any) {
            this.favorito++
            this.mensagem = `${filme.nome} adicionado ao favoritos :)`
            setTimeout(() => {
                this.mensagem = ''
            }, 3000)
        }
    },

    components: { FilmeItem }
}

</script>

<template>
    <div class="container">
        <FilmeItem v-for="(item, index) in listaDeFilmes" :key="index" :filme="item"
            @adicionar-ao-favorito="adicionadoAoFavoritos" />
    </div>
    <div v-if="mensagem">
        <p>{{ mensagem }}</p>
    </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
  padding: 20px;
  background: #f8f9fa;
}

.mensagem {
  text-align: center;
  margin-top: 20px;
  font-size: 16px;
  font-weight: bold;
  color: #28a745;
}
</style>
<script>
export default {
    props: {
        filme: { type: Object, required: true }
    },
    data() {
        return {
            mostrarDescricao: false
        }
    },

    methods: {
        addFavoritos() { this.$emit('adicionar-ao-favorito', this.filme) },
        descricaoAmostra() {
            this.mostrarDescricao = !this.mostrarDescricao
        }
    }
}
</script>

<template>
    <section class="corpo-container">
        <h1 class="titulo-filme">{{ filme.nome }}</h1>
        <p class="ano-filme">{{ filme.ano }}</p>
        <img :src="filme.imagem">

        <div class="buttons">
            <button class="detalhes" @click="descricaoAmostra"> Ver Detalhes </button>
            <button class="favoritos" @click="addFavoritos"> Adicionar ao Favoritos </button>
        </div>
    </section>

    <div v-if="mostrarDescricao">
        <p>{{ filme.descricao }}</p>
    </div>

</template>

<style scoped>
.corpo-container {
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  padding: 16px;
  width: 250px;
  text-align: center;
  transition: transform 0.2s;
}

.corpo-container:hover {
  transform: translateY(-5px);
}

.corpo-container img {
  width: 100%;
  border-radius: 8px;
  margin-bottom: 12px;
}

.titulo-filme {
  font-size: 18px;
  font-weight: 600;
  margin-bottom: 4px;
  color: #333;
}

.ano-filme {
  font-size: 14px;
  color: #777;
  margin-bottom: 10px;
}

.descricao-filme {
  font-family: 'Poppins', sans-serif; /* Fonte moderna */
  font-size: 15px;
  font-weight: 400;
  color: #555; /* Cinza suave */
  text-align: justify;
  line-height: 1.6; /* Espaçamento confortável */
  background: #f9f9f9; /* Fundo clarinho */
  padding: 10px;
  border-radius: 8px;
  margin-top: 12px;
  box-shadow: inset 0 1px 4px rgba(0, 0, 0, 0.05);
  white-space: normal;  
  word-wrap: break-word; 
  max-width: 600px;   
}

.buttons {
  display: flex;
  justify-content: space-between;
  margin-top: 12px;
}

.buttons button {
  flex: 1;
  margin: 0 4px;
  padding: 8px 12px;
  border: none;
  border-radius: 6px;
  color: #fff;
  font-size: 14px;
  cursor: pointer;
  transition: background 0.3s;
}

.detalhes {
  background: #007bff;
}

.detalhes:hover {
  background: #0056b3;
}

.favoritos {
  background: #e74c3c;
}

.favoritos:hover {
  background: #c0392b;
}
</style>
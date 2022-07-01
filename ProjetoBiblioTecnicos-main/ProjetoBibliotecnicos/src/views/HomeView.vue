<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      Livros: [
        { id: "72b60663-4943-4f37-a782-3b0688d5b313", nome: "Livro 1", autor: "Pessoa 1", data: "XX-XX-20XX" },
        { id: "e91ca40f-1b1c-40d9-a589-a6d74b42f6c5", nome: "Livro 2", autor: "Pessoa 2", data: "XX-XX-19XX" },
        { id: "d181a6a6-fa46-426e-bd5a-9a9ee19356d6", nome: "Livro 3", autor: "Pessoa 3", data: "XX-XX-20XX" },
        { id: "e0b9c7d6-06d5-405f-a674-0e4b286a6b6a", nome: "Livro 4", autor: "Pessoa 4", data: "XX-XX-20XX" },
        { id: "0daa3bee-b872-4ca7-87ef-42481f434a9a", nome: "Livro 5", autor: "Pessoa 5", data: "XX-XX-19XX" },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_livro !== "") {
        const novo_id = uuidv4();
        this.Livros.push({
          id: novo_id,
          nome: this.novo_livro,
          autor: this.livro_autor,
          data: this.livro_data
      });
      this.novo_livro = "";
      }
    },
    excluir(livro) {
      const indice = this.Livros.indexOf(livro);
      this.Livros.splice(indice, 1);
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de Livros</h2>
    </div>
    <div class="form-input">
      <input class="LivroInput" placeholder="Nome:" type="text" v-model="novo_livro" />
      <br>
      <input class="LivroInput" placeholder="Autor:" type="text" v-model="livro_autor" />
      <br>
      <input class="LivroInput" type="date" v-model="livro_data" />
      <button class="BtnSalvar" @click="salvar">Salvar</button>
    </div>
  </div>

  <div class="LivroWrapper">
    <div class="BoxLivro" v-for="Livros in Livros" :key="Livros.id">
      <div>ID: {{ Livros.id }}</div>
      <div>Nome: {{ Livros.nome }}</div>
      <div>Autor: {{ Livros.autor }}</div>
      <div>Data: {{ Livros.data }}</div>
      <button class="BtnEdit">Editar</button>
      <button class="BtnEdit" @click="excluir(Livros)">Excluir</button>
    </div>
  </div>
  <div class="Bottom"></div>
</template>

<style scoped>
.Bottom {
  height: 10vh;
}
.BoxLivro {
  width: 100%;
  box-shadow: 0.5px 0.5px 2.5px black;
  padding: 1rem;
  margin-bottom: 1vh;
}
.container{
  margin: 10px;
  margin-left: 10px
}
.LivroInput{
  margin-right: 10px;
  margin-bottom: 10px;
  outline: 1px solid black ;
  border-radius: 1px ;
}
.BtnSalvar{
  margin-left: 0.45vh;
}
.BtnEdit{
  margin-right: 3px;
  margin-top: 3px;
}
</style>

<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      Autores: [
        { id: "72b60663-4943-4f37-a782-3b0688d5b313", nome: "A",},
        { id: "e91ca40f-1b1c-40d9-a589-a6d74b42f6c5", nome: "Livro 2",},
        { id: "d181a6a6-fa46-426e-bd5a-9a9ee19356d6", nome: "Livro 3",},
        { id: "e0b9c7d6-06d5-405f-a674-0e4b286a6b6a", nome: "Livro 4",},
        { id: "0daa3bee-b872-4ca7-87ef-42481f434a9a", nome: "Livro 5",},
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_autor !== "") {
        const novo_id = uuidv4();
        this.Livros.push({
          id: novo_id,
          nome: this.novo_autor,
          nasc: this.autor_nasc,
      });
      this.novo_autor = "";
      }
    },
    excluir(livro) {
      const indice = this.Autores.indexOf(autor);
      this.Autores.splice(indice, 1);
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de Autores</h2>
    </div>
    <div class="form-input">
      <input class="LivroInput" placeholder="Nome:" type="text" v-model="novo_autor" />
      <br>
      <input class="LivroInput" type="date" v-model="autor_nasc" />
      <button class="BtnSalvar" @click="salvar">Salvar</button>
    </div>
  </div>

  <div class="LivroWrapper">
    <div class="BoxLivro" v-for="Livros in Autores" :key="Autores.id">
      <div>ID: {{ Autores.id }}</div>
      <div>Nome: {{ Autores.nome }}</div>
      <div>Data de Nascimento: {{ Autores.nasc }}</div>
      <button class="BtnEdit">Editar</button>
      <button class="BtnEdit" @click="excluir(Autores)">Excluir</button>
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

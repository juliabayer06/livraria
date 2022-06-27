<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      novo_livro: "",
      livros: [
        { id: "bbf13e16-8a92-49da-b37b-9f1f218bc384", name: "Livro 1" },
        { id: "46ec141f-f35b-4e50-b60d-3db9d6a6022a", name: "Livro 2" },
        { id: "6392406d-6273-44fd-814b-c45f4c6aed9f", name: "Livro 3" },
        { id: "978145ff-0026-475e-adc7-5029786bb6ce", name: "Livro 4" },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_livro !== "") {
        const novo_id = uuid();
        this.livros.push({
          id: novo_id,
          name: this.novo_livro,
        });
        this.novo_livro = "";
      }
    },
    excluir(livro) {
      const indice = this.livros.indexOf(livro);
      this.livros.splice(indice, 1);
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de livros</h2>
    </div>
    <div class="form-input">
      <input
        type="text"
        v-model="novo_categoria"
        @keyup.enter="salvar"
        placeholder="Categorias"
      />
      <input
        type="text"
        v-model="novo_livro"
        @keyup.enter="salvar"
        placeholder="Livros"
      />
      <button @click="salvar">Salvar</button>
    </div>
  </div>
  <div class="list-items">
    <table>
      <thead>
        <tr>
          <td>ID</td>
          <td>Nome</td>
          <td>Categorias</td>
          <td>Ações</td>
        </tr>
      </thead>

      <tbody>
        <tr v-for="livro in livros" :key="livro.id">
          <td>{{ livro.id }}</td>
          <td>{{ livro.name }}</td>
          <td>{{ livro.categoria }}</td>
          <td>
            <button>Editar</button>
            <button @click="excluir(categoria)">Apagar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<style>

</style>

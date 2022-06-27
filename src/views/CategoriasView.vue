<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      novo_categoria: "",
      categorias: [
        { id: "bbf13e16-8a92-49da-b37b-9f1f218bc384", name: "Categoria 1" },
        { id: "46ec141f-f35b-4e50-b60d-3db9d6a6022a", name: "Categoria 2" },
        { id: "6392406d-6273-44fd-814b-c45f4c6aed9f", name: "Categoria 3" },
        { id: "978145ff-0026-475e-adc7-5029786bb6ce", name: "Categoria 4" },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_categoria !== "") {
        const novo_id = uuid();
        this.categorias.push({
          id: novo_id,
          name: this.novo_categoria,
        });
        this.novo_categoria = "";
      }
    },
    excluir(categoria) {
      const indice = this.categorias.indexOf(categoria);
      this.categorias.splice(indice, 1);
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de categorias</h2>
    </div>
    <div class="form-input">
      <input
        type="text"
        v-model="novo_categoria"
        @keyup.enter="salvar"
        placeholder="Categorias"
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
          <td>Ações</td>
        </tr>
      </thead>

      <tbody>
        <tr v-for="categoria in categorias" :key="categoria.id">
          <td>{{ categoria.id }}</td>
          <td>{{ categoria.name }}</td>
          <td>
            <button>Editar</button>
            <button @click="excluir(categoria)">Apagar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style></style>

<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      novo_autor: "",
      nova_idade: "",
      autores: [
        {
          id: "bbf13e16-8a92-49da-b37b-9f1f218bc384",
          name: "Autor 1",
          idade: "90",
        },
        {
          id: "46ec141f-f35b-4e50-b60d-3db9d6a6022a",
          name: "Autor 2",
          idade: "44",
        },
        {
          id: "6392406d-6273-44fd-814b-c45f4c6aed9f",
          name: "Autor 3",
          idade: "23",
        },
        {
          id: "978145ff-0026-475e-adc7-5029786bb6ce",
          name: "Autor 4",
          idade: "57",
        },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_autor !== "") {
        const novo_id = uuid();
        this.autores.push({
          id: novo_id,
          name: this.novo_autor,
          idade: this.nova_idade,
        });
        this.novo_autor = "";
        this.nova_idade = "";
      }
    },
    excluir(autor) {
      const indice = this.autores.indexOf(autor);
      this.autores.splice(indice, 1);
      this.idade.splice(indice, 1);
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
      <input type="text" v-model="novo_autor" placeholder="Nome do autor" />
      <input
        type="text"
        v-model="nova_idade"
        @keyup.enter="salvar"
        placeholder="Idade do autor"
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
          <td>Idade</td>
          <td>Ações</td>
        </tr>
      </thead>

      <tbody>
        <tr v-for="autor in autores" :key="autor.id">
          <td>{{ autor.id }}</td>
          <td>{{ autor.name }}</td>
          <td>{{ autor.idade }}</td>
          <td>
            <button>Editar</button>
            <button @click="excluir(autor)">Apagar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style></style>

<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      novo_editora: "",
      novo_site: "",
      editoras: [
        {
          id: "bbf13e16-8a92-49da-b37b-9f1f218bc384",
          name: "Galera",
          site: "www.record.com.br",
        },
        {
          id: "46ec141f-f35b-4e50-b60d-3db9d6a6022a",
          name: "Faro Editorial",
          site: "www.amazon.com.br",
        },
        {
          id: "6392406d-6273-44fd-814b-c45f4c6aed9f",
          name: "Principis",
          site: "www.amazon.com.br",
        },
        {
          id: "978145ff-0026-475e-adc7-5029786bb6ce",
          name: "Record",
          site: "www.record.com.br",
        },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_editora !== "") {
        const novo_id = uuid();
        this.editoras.push({
          id: novo_id,
          name: this.novo_editora,
          site: this.novo_site,
        });
        this.novo_editora = "";
        this.novo_site = "";
      }
    },
    excluir(editora) {
      const indice = this.editoras.indexOf(editora);
      this.editoras.splice(indice, 1);
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de editoras</h2>
    </div>
    <div class="form-input">
      <input type="text" v-model="novo_editora" placeholder="Nome da editora" />
      <input
        type="text"
        v-model="novo_site"
        @keyup.enter="salvar"
        placeholder="Site da editora"
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
          <td>Sites</td>
          <td>Ações</td>
        </tr>
      </thead>

      <tbody>
        <tr v-for="editora in editoras" :key="editora.id">
          <td>{{ editora.id }}</td>
          <td>{{ editora.name }}</td>
          <td>{{ editora.site }}</td>
          <td>
            <button>Editar</button>
            <button @click="excluir(editora)">Apagar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style></style>

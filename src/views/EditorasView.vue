<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      novo_editora: "",
      editoras: [
        { id: "bbf13e16-8a92-49da-b37b-9f1f218bc384",name: "Editora 1",site: "www.editora1.com",},
        { id: "46ec141f-f35b-4e50-b60d-3db9d6a6022a",name: "Editora 2",site: "www.editora2.com",},
        { id: "6392406d-6273-44fd-814b-c45f4c6aed9f",name: "Editora 3",site: "www.editora3.com",},
        { id: "978145ff-0026-475e-adc7-5029786bb6ce",name: "Editora 4",site: "www.editora4.com",},
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
        });
        this.novo_editora = "";
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
      <input
        type="text"
        v-model="novo_editora"
        @keyup.enter="salvar"
        placeholder="Editoras"
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

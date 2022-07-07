<script>
import { v4 as uuid} from "uuid";
export default {
  data() {
    return {
      novo_jogador: "",
      novo_time: "",
      jogadores: [
        { id: "9a7c7c02-874d-4556-8a13-4a33c56571d1", name: "Jogador 1", timeid: "1" },
        { id: "475f6d39-5a56-4442-8a2d-5ceba6b4b807", name: "Jogador 2", timeid: "2" },
        { id: "874b37b6-3546-4c05-bc54-5d0fdb886d16", name: "Jogador 3", timeid: "3" },
        { id: "9b35ce67-a4ec-45a0-be67-1983e37bd723", name: "Jogador 4", timeid: "4" },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_jogador !== ""){
      const novo_id=uuid();
      this.jogadores.push({
        id: novo_id,
        name: this.novo_jogador,
        timeid: this.novo_time,
      });
        this.novo_jogador = "";
        this.novo_time = "";
      }
    },
    excluir(jogador){
      const indice = this.jogadores.indexOf(jogador);
      this.jogadores.splice(indice, 1);
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de Jogadores</h2>
    </div>
    <div class="form-input">
      <input type="text" placeholder="Nome" v-model="novo_jogador" @keypress.enter="salvar" />
      <input type="text" placeholder="Time ID" v-model="novo_time" @keypress.enter="salvar" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-items">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Time ID</th>
            <th>Ação</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="jogador in jogadores" :key="jogador.id">
            <td>{{jogador.id}}</td>
            <td>{{jogador.name}}</td>
            <td>{{jogador.timeid}}</td>
            <td>
              <button>Editar</button>
              <button @click="excluir(jogador)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<style></style>

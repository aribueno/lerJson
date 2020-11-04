<template>
  <b-container>
    <h2>{{ titulo }}</h2>
    <hr>
    <b-table-simple small id="tabela-resumo">
      <b-thead head-variant="dark">
        <b-tr>
          <b-th class="text-left">Participante</b-th>
          <b-th class="text-right">Pago Pago</b-th>
          <b-th class="text-right">Pago à Receber</b-th>
        </b-tr>
      </b-thead>
      <b-tbody>
        <b-tr v-for="participante in listaResumo" :key="participante.Id">
          <b-th class="text-left">{{ participante.nome }}</b-th>
          <b-th class="text-right">R$ {{ participante.valorpago }}</b-th>
          <b-th class="text-right">R$ {{ participante.valorreceber }}</b-th>
        </b-tr>
      </b-tbody>
    </b-table-simple>
  </b-container>
</template>

<script>
export default {
  data() {
    return {
      titulo: "Resumo das Contas",
      listaResumo: [],
    };
  },
  methods: {
    pegaLista() {
      fetch("../dados/resumo.json")
        .then((response) => response.json())
        .then((data) => (this.listaResumo = data))
    },
    pegaResumo() {
      fetch("../public/dados/resumo.json")
        .then((response) => {
          console.log(response)
          return response.json()
        })
        .then((data) => {
          // Work with JSON data here
          console.log(data)
        })
        .catch((err) => {
          // Do something for an error here
          console.log("Error Reading data " + err)
        })
    }
  },
  mounted() {
    this.pegaLista();
    // this.pegaResumo()
  },
};
</script>

<style>
    .container {
        margin-top: 20px;
    }

    #tabela-resumo{
        width: 500px;
        margin: 0 auto;
        margin-top: 20px;
    }

</style>
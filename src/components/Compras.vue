<template>
  <b-container>
    <h2>{{ titulo }}</h2>
    <hr />

    <b-form id="form-compras">
      <b-form-group
        label-cols-sm="3"
        label="Descrição:"
        label-align-sm="right"
        label-for="descricao"
      >
        <b-form-input v-model="descricao" id="descricao"></b-form-input>
      </b-form-group>

      <b-form-group
        label-cols-sm="3"
        label="Data Compra:"
        label-align-sm="right"
        label-for="data"
      >
        <b-form-input v-model="dataCompra" id="data" type="date"></b-form-input>
      </b-form-group>

      <b-form-group
        label-cols-sm="3"
        label="Valor:"
        label-align-sm="right"
        label-for="valor"
      >
        <b-form-input v-model="valor" id="valor" type="number"></b-form-input>
      </b-form-group>

      <b-form-group
        label-cols-sm="3"
        label="Quem pagou:"
        label-align-sm="right"
        label-for="quempagou"
      >
        <b-form-select v-model="selecionado">
          <option v-for="participante in quemPagou" :key="participante.nome">
            {{ participante.nome }}
          </option>
        </b-form-select>
      </b-form-group>

      <b-form-group>
        <div>
          <b-button class="botoes" @click="incluirCompra()" variant="success"
            >Gravar</b-button
          >
          <b-button class="botoes" variant="success">Voltar</b-button>
        </div>
      </b-form-group>
    </b-form>
  </b-container>
</template>

<script>
// import GravarJSON from '../utils/GravarJSON'

export default {
  data() {
    return {
      titulo: "Compras",
      descricao: "",
      dataCompra: "",
      valor: 0,
      quemPagou: [],
      selecionado: "",
      compras: [],
    };
  },
  methods: {
    incluirCompra() {
      // Monta o registro json
      const compra = `
            {
                "descricao": "${this.descricao}",
                "data": ${this.dataCompra},
                "valor": ${this.valor},
                "quempagou": "${this.selecionado}"
            }   
        `;

      var fs = require("fs");

      var data = "New File Contents";

      fs.writeFile("temp.txt", data, (err) => {
        if (err) console.log(err);
        console.log("Successfully Written to File.");
      });

      // fs.readFile("../dados/compras.json", (err, data) => {
      //   if (err) throw err;
      //   console.log(data);
      // });

      // fs.readFile('../dados/compras.json', 'utf8', function readFileCallback(err, data){
      //     if (err){
      //         console.log(err)
      //     } else {
      //       console.log(data)
      //         // obj = JSON.parse(compra); //now it an object
      //         // obj.this.compras.push({id: 2, square:3}); //add some data
      //         // json = JSON.stringify(obj); //convert it back to json
      //         // fs.writeFile('../public/dados/compras.json', json, 'utf8', callback); // write it back
      //     }})

      console.log(compra);
      // console.log(this.descricao);
      // console.log(this.selecionado);
      // console.log(compra);
    },
    carregarParticipante() {
      fetch("../dados/participantes.json")
        .then((response) => response.json())
        .then((data) => (this.quemPagou = data));
    },
    carregaCompras() {
      fetch("../dados/compras.json")
        .then((response) => response.json())
        .then((data) => (this.compras = data));
    },
  },
  mounted() {
    this.carregarParticipante();
    this.carregaCompras();
  },
};
</script>

<style>
.b-container {
  margin-top: 20px;
}

#form-compras {
  width: 50%;
  margin: 0 auto;
  margin-top: 20px;
  text-align: center;
}

.botoes {
  margin-right: 10px;
  margin-top: 20px;
  width: 100px;
}
</style>
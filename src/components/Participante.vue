<template>
  <b-container>
    <h2>Participante</h2>
    <hr />

    <div>
      <b-form id="form-participante">
        <b-form-group
          label-cols-sm="3"
          label="Nome:"
          label-align-sm="right"
          label-for="nome"
        >
          <b-form-input id="nome"></b-form-input>
        </b-form-group>

        <b-form-group
          label-cols-sm="3"
          label="Telefone:"
          label-align-sm="right"
          label-for="telefone"
        >
          <b-form-input id="telefone"></b-form-input>
        </b-form-group>

        <b-form-group
          label-cols-sm="3"
          label="E-mail:"
          label-align-sm="right"
          label-for="email"
        >
          <b-form-input type-email id="email"></b-form-input>
        </b-form-group>

        <b-form-group
          label-cols-sm="3"
          label="Qtde pessoas:"
          label-align-sm="right"
          label-for="qtdepessoas"
        >
          <b-form-input type-number sm id="qtdepessoas"></b-form-input>
        </b-form-group>


        <b-button class="botoes" variant="success">Gravar</b-button>
        <b-button class="botoes" variant="success">Voltar</b-button>


      </b-form>
    </div>
  </b-container>
</template>

<script>
export default {};
</script>

<style>
.container {
  margin-top: 20px;
}

.hr{
    border: 1 solid black;
}

#form-participante {
  width: 60%;
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
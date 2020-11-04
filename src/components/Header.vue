<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand>Divisão de Contas</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item to='/'>Resumo</b-nav-item>
          <b-nav-item to='/participante'>Participante</b-nav-item>
          <b-nav-item to='/compras'>Compras</b-nav-item>
        </b-navbar-nav>


      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {};
</script>

<style>
</style>
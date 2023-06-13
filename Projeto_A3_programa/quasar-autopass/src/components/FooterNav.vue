<template>
  <footer class="botoes-footer-compra">
    <router-link
      to="/produtos"
      class="botao-link-nav"
    >
      <q-icon
        name="arrow_left"
        class="border-circle"
      />
      Voltar
    </router-link>
    <router-link
      to="/"
      class="botao-link-nav"
    >
      <q-icon
        name="close"
        class="border-circle"
      />
      Cancelar
    </router-link>
  </footer>
</template>

<style lang="sass">
.botoes-footer-compra
  display: flex
  width: 75%
  justify-content: space-between
</style>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'FooterNav',
  components: {},
});
</script>

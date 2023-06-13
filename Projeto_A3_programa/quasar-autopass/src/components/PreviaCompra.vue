<template>
  <section
    class="pagamento-container"
    v-if="this.$route.params.tipoPagamento !== 'unitario'"
  >
    <h1>Insira seu {{ tipoPagamento }}</h1>
    <img
      src="../assets/icone-cartao-removebg-preview.png"
      alt="icone de cartão"
      class="cartao-icone"
    />
  </section>
  <FooterNav></FooterNav>
</template>

<style lang="sass">
.pagamento-container
  display: flex
  flex-flow: column nowrap
  align-items: center

.cartao-icone
  width: 25%
</style>

<script>
import { defineComponent } from 'vue';
import FooterNav from './FooterNav.vue';

export default defineComponent({
  name: 'PreviaCompra',
  components: { FooterNav },
  props: {
    tipoPagamento: {
      type: String,
      required: true,
    },
  },
});
</script>

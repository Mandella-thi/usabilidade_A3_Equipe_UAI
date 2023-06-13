<template>
  <section class="produtos-container">
    <h1>Selecione o Produto</h1>
    <div class="botoes-container">
      <BotaoLink
        v-for="botao in botoes"
        :key="botao.novaRota"
        :textoBotao="botao.textoBotao"
        :novaRota="botao.novaRota"
        :classe="'botao-link-produto'"
        :tipoPagamento="botao.tipoPagamento"
      />
    </div>
    <footer class="botoes-footer">
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
  </section>
</template>

<style lang="sass">
@import '../css/Produtos.sass'
</style>

<script>
import { defineComponent } from 'vue';
import BotaoLink from 'src/components/BotaoLink.vue';

export default defineComponent({
  name: 'ProdutosPage',
  components: {
    BotaoLink,
  },
  data() {
    return {
      botoes: [
        {
          textoBotao: 'Cartão TOP',
          novaRota: '/compra/cartao-top',
          tipoPagamento: 'Cartão TOP',
        },
        {
          textoBotao: 'Bilhete Único',
          novaRota: '/compra/bilhete-unico',
          tipoPagamento: 'bilhete-unico',
        },
        {
          textoBotao: 'Unitário',
          novaRota: '/compra/unitario',
          tipoPagamento: 'unitario',
        },
      ],
    };
  },
});
</script>

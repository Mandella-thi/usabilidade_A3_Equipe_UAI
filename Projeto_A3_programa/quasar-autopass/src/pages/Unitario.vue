<template>
  <section>
    <h1>Selecione a Opção</h1>
    <div class="unitario-container">
      <BotaoLink
        v-for="botao in botoes"
        :key="botao.novaRota"
        :textoBotao="botao.textoBotao"
        :novaRota="botao.novaRota"
        :classe="'botao-link-produto'"
        :tipoPagamento="botao.tipoPagamento"
      />
    </div>
  </section>
</template>

<style lang="sass"></style>

<script>
import { defineComponent } from 'vue';
import BotaoLink from 'src/components/BotaoLink.vue';

export default defineComponent({
  name: 'UnitarioPage',
  components: {},
  data() {},
});
</script>

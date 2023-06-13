<template>
  <PreviaCompra
    v-if="!pagamentoInserido && parseiaRotaPagamento() !== 'unitario'"
    :tipoPagamento="parseiaRotaPagamento()"
  ></PreviaCompra>
  <Pagamentos
    v-if="pagamentoInserido || parseiaRotaPagamento() == 'unitario'"
  ></Pagamentos>
</template>

<script>
import PreviaCompra from 'src/components/PreviaCompra.vue';
import Pagamentos from './Pagamentos.vue';
import { defineComponent, ref, onMounted } from 'vue';
export default defineComponent({
  name: 'CompraPage',
  components: { PreviaCompra, Pagamentos },
  setup() {
    const pagamentoInserido = ref(false);

    onMounted(() => {
      if (window.location.href.includes('unitario')) {
        pagamentoInserido.value = true;
      } else {
        setTimeout(() => {
          pagamentoInserido.value = true;
        }, 2000);
      }
    });

    return {
      pagamentoInserido,
    };
  },
  methods: {
    parseiaRotaPagamento() {
      const rotas = { 'cartao-top': 'Cartão TOP', 'bilhete-unico': 'Bilhete Único' };
      const tipoPagamento = this.$route.params.tipoPagamento;
      return rotas[tipoPagamento] || '';
    },
  },
});
</script>

<template>
  <router-link :to="novaRota">
    <q-btn
      :label="textoBotao"
      :class="ComputedClasse"
      @click="redirecionaCompra"
    >
    </q-btn>
  </router-link>
</template>

<script>
export default {
  name: 'BotaoLink',
  props: {
    textoBotao: {
      type: String,
      required: true,
    },
    novaRota: {
      type: String,
      required: true,
    },
    classe: {
      type: String,
      required: false,
    },
    icone: {
      type: String,
      required: false,
    },
    tipoPagamento: {
      type: String,
      required: true,
    },
  },
  computed: {
    ComputedClasse() {
      let classes = {};
      classes[this.classe] = true;
      return classes;
    },
  },
  methods: {
    redirecionaCompra() {
      if (['cartao-top', 'bilhete-unico'].includes(this.tipoPagamento)) {
        this.$router.push({
          name: 'compra',
          params: {
            tipoPagamento: this.tipoPagamento,
          },
        });
      } else {
        this.$router.push(this.novaRota);
      }
    },
  },
};
</script>

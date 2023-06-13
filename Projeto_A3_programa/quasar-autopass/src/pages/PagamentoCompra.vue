<template>
  <section
    class="pagamento-container"
    v-if="this.formaEscolhida == null"
  >
    <h1 style="margin-bottom: 20px; text-align: center">
      Selecione uma forma de pagamento
    </h1>
    <section class="formas-pagamento-container">
      <button
        v-for="item in formasPagamento"
        :key="item.label"
        class="botao-preco"
        :class="{ active: item.value === preco }"
        @click="escolheFormaPagamento(item.value)"
      >
        {{ item.label }}
      </button>
    </section>
  </section>
  <section v-else-if="this.formaEscolhida && !inserirOpcao">
    <h1>Opção {{ this.formaEscolhida }} Selecionado!</h1>
  </section>
  <section
    v-else-if="
      this.formaEscolhida &&
      this.formaEscolhida !== 'Pix' &&
      this.inserirOpcao &&
      !this.loading
    "
    class="inserir-container"
  >
    <h1>Insira o {{ this.formaEscolhida }}</h1>
    <img
      src="../assets/icone-cartao-removebg-preview.png"
      alt="icone-cartao"
    />
    <h3
      v-if="this.formaEscolhida == 'Dinheiro'"
      style="margin-top: 30px"
    >
      Não há devolução de troco
    </h3>
  </section>

  <section
    v-else-if="
      this.formaEscolhida &&
      this.inserirOpcao &&
      this.loading &&
      this.formaEscolhida !== 'Pix'
    "
  >
    <h1 v-if="!this.pagamentoEfetuado">
      Aguarde {{ this.formaEscolhida === 'Pix' ? 'geração do QR code' : '' }}...
    </h1>

    <section
      v-else-if="this.pagamentoEfetuado"
      class="pagamento-efetuado-container"
    >
      <h1 style="margin-bottom: 60px">Transação Concluída</h1>
      <h4>Aguarde impressão do Comprovante</h4>
    </section>
  </section>
  <section
    v-else-if="
      this.formaEscolhida &&
      this.inserirOpcao &&
      this.loading &&
      this.formaEscolhida === 'Pix'
    "
  >
    <h1 v-if="!this.pagamentoEfetuado">
      Aguarde {{ this.formaEscolhida === 'Pix' ? 'geração do QR code' : '' }}...
    </h1>
    <section
      v-else-if="this.pagamentoEfetuado"
      class="pagamento-efetuado-container"
    >
      <h1 style="margin-bottom: 60px">Transação Concluída</h1>
      <h4>Aguarde impressão do Comprovante</h4>
    </section>
    <section v-else-if="this.QRCodegerado">
      <h1>Scaneie a tela</h1>
    </section>
  </section>

  <FooterNav />
</template>

<style lang="sass">
@import '../css/PagamentoCompra'
</style>

<script>
import { defineComponent } from 'vue';
import FooterNav from 'src/components/FooterNav.vue';

export default defineComponent({
  name: 'PagamentosPage',
  components: { FooterNav },
  data() {
    return {
      formasPagamento: [
        { label: 'Débito', value: 'Débito' },
        { label: 'Crédito', value: 'Crédito' },
        { label: 'Dinheiro', value: 'Dinheiro' },
        { label: 'Pix', value: 'Pix' },
      ],
      formaEscolhida: null,
      inserirOpcao: null,
      pagamentoEfetuado: false,
      loading: false,
      geraQRCode: false,
      QRCodegerado: false,
    };
  },
  methods: {
    escolheFormaPagamento(valor) {
      this.formaEscolhida = valor;
      if (valor === 'Pix') {
        this.inserirOpcao = true;
        this.loading = true;
      }
    },
  },
  watch: {
    formaEscolhida(novoValor) {
      if (novoValor !== 'Pix')
        setTimeout(() => {
          this.inserirOpcao = true;
        }, 2000);
    },
    inserirOpcao(novoValor) {
      if (this.formaEscolhida !== 'Pix') {
        console.log('mudou inserir');
        setTimeout(() => {
          this.loading = true;
        }, 1500);
      }
    },
    loading(novoValor) {
      console.log('mudou loading');
      if (this.formaEscolhida !== 'Pix') {
        setTimeout(() => {
          this.pagamentoEfetuado = true;
        }, 3000);
      } else {
        setTimeout(() => {
          this.geraQRCode = true;
        }, 3000);
      }
    },
    geraQRCode(novoValor) {
      setTimeout(() => {
        this.QRCodegerado = true;
      }, 3000);
    },
    QRCodegerado(novoValor) {
      setTimeout(() => {
        this.pagamentoEfetuado = true;
      }, 3000);
    },
  },
});
</script>

<template>
  <header>
    <Navbar></Navbar>
  </header>
  <section class="layout-flex">
    <router-view />
  </section>
</template>

<style lang="sass">
@import "../css/app.sass"
</style>

<script>
import { defineComponent, ref } from 'vue';
import Navbar from 'src/components/Navbar.vue';

export default defineComponent({
  name: 'MainLayout',

  components: {
    Navbar,
  },
});
</script>

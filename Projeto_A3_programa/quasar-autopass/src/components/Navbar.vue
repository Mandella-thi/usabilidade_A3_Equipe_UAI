<template>
  <nav class="navbar">
    <q-icon
      name="explore"
      size="md"
    />
    <img
      class="nav-item"
      src="../assets/autopass-icon.png"
      alt="Logo da Autopass"
    />
  </nav>
</template>

<style lang="sass">
@import "../css/Navbar"
</style>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'NavbarMain',
  props: {
    link: {
      type: String,
      default: 'jose',
    },
  },
});
</script>

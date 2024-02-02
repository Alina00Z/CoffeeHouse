<template>
  <div style="position: relative; height: 100vh; width: 100vw;">
    <div ref="backdrop" class="backdrop bg-backdrop"></div>
    <modal-card @close-modal="closeModal() " v-if="card_selected !== null" :card=card_selected></modal-card>
    <header-component @click-coffee-menu="isMenuActive = $event"/>
    <Nuxt v-if="!isMenuActive"/>
    <!-- :class="{
      'not-active' : isMenuActive
    }"
    -->
    <coffee-menu @click-card="clickCard" v-if="isMenuActive"/>
    <footer-component />

  </div>
  
</template>

<style>
  .backdrop {
    position: fixed;
    z-index: 2;
    width: 100vw;
    height: 0vh;
    opacity: 0%;

    transition: height 0.6s ease-in-out, opacity 0.6s ease-in-out 0.1s;
  }
  .backdrop.active {
    height: 100vh;
    opacity: 80%;
  }
</style>

<script>
import HeaderComponent from '/components/Header.vue'
import FooterComponent from '/components/Footer.vue'
import CoffeeMenu from '/components/CoffeeMenu.vue'
import ModalCard from '/components/ModalCard.vue'
export default {
  components: {
    HeaderComponent,
    FooterComponent,
    CoffeeMenu,
    ModalCard
  },
  data() {
    return {
      isMenuActive: false,
      card_selected: null
    }
  },
  methods: {
    clickCard([type, name, info, price]) {
      const body = document.querySelector('body');
      body.style.overflow = 'hidden';
      this.$refs.backdrop.classList.add('active');

      this.card_selected = {type: type, name: name, info: info, price: price};
    },
    closeModal() {
      this.card_selected = null;
      const body = document.querySelector('body');
      body.style.overflow = 'visible';
      this.$refs.backdrop.classList.remove('active');
    }
  }
}
</script>

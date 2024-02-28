<template>
  <div id="defaultApp" style="position: relative;">
    <div ref="backdrop" class="backdrop bg-backdrop" @click="closeModal()"></div>

    <modal-card @close-modal="closeModal()" v-if="card_selected !== null" :card=card_selected></modal-card>

    <header-component :is-burger-active-prop="isBurgerActive" @click-burger="clickBurger($event)" @click-menu="openMenu()" @close-burger="closeBurger()"/>
    
    <Nuxt/> 
  
    <footer-component id="footer"/>  
  </div>
  
</template>

<style>
  .backdrop {
    position: fixed;
    top: 0px;
    left: 0px;
    z-index: 11;
    width: 100%;
    height: 0%;
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
import ModalCard from '/components/ModalCard.vue'
export default {
  components: {
    HeaderComponent,
    FooterComponent,
    ModalCard,
},
  created () {
    this.$nuxt.$on('click-card', ($event) => this.clickCard($event));
  },
  destroyed() {
    this.$nuxt.$off('click-card', ($event) => this.clickCard($event));
  },
  data() {
    return {
      isMenuActive: false,
      card_selected: null,
      isBurgerActive: false
    }
  },
  methods: {
    clickCard([type, name, info, price]) {
      const body = document.querySelector('body');
      body.style.overflow = 'hidden';
      this.$refs.backdrop.classList.add('active');

      this.card_selected = {type: type, name: name, info: info, price: price};

      const defaultApp = document.querySelector('.defaultApp');
    },
    closeModal() {
      this.card_selected = null;
      const body = document.querySelector('body');
      body.style.overflow = 'visible';
      this.$refs.backdrop.classList.remove('active');
    },
    clickBurger(event) {
      this.isBurgerActive = event;
      const body = document.querySelector('body');
      // for scroll - none
      if (this.isBurgerActive) {
        body.style.overflow = 'hidden';
      }
      else {
        this.closeBurger();
      }
    },
    closeBurger() {
      const body = document.querySelector('body');
      body.style.overflow = 'visible';
      this.isBurgerActive = false;
    },
    openMenu() {
      this.closeBurger();
      this.isMenuActive = true;
    },
    openIndex() {
      closeBurger();
      this.isMenuActive = false;
    }
  }
}
</script>

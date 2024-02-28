<template>
  <div id="defaultApp" style="position: relative;">

    <div ref="backdrop" class="backdrop bg-backdrop" @click="closeModal()"></div>
    <modal-card @close-modal="closeModal()" v-if="card_selected !== null" :card=card_selected></modal-card>
    <header-component @click-burger="clickBurger" @click-menu="isMenuActive = $event"/>
    <!-- burger -->
    <div v-if="isBurgerActive" class="container">
      <div class="burger_menu color-dark burger-link">
        <ul class="burger_menu-navbar">
          <li class="btn menu_item">
            <div class="menu_item-main">
              <div class="menu_item-main-word">Favorite coffee</div>
            </div>  
            <div class="line_down-hover"></div>
          </li>
          <li class="btn menu_item">
            <div class="menu_item-main">
              <div class="menu_item-main-word">About</div>
            </div>  
            <div class="line_down-hover"></div>
          </li>
          <li class="btn menu_item">
            <div class="menu_item-main">
              <div class="menu_item-main-word">Mobile app</div>
            </div>  
            <div class="line_down-hover"></div>
          </li>
          <li class="btn menu_item">
            <div class="menu_item-main">
              <div class="menu_item-main-word">Contact us</div>
            </div>  
            <div class="line_down-hover"></div>
          </li>
        </ul>
        <li class="btn menu_item" @click="clickMenu()">
            <div class="menu_item-main">
              <div class="menu_item-main-word">Menu</div>
              <div class="menu_item-main-icon"></div>
            </div>  
            <div class="line_down-hover"></div>
          </li>
      </div>
    </div>
    <Nuxt/> 
    <!-- :class="{  v-if="!isMenuActive"
      'not-active' : isMenuActive
    }"
    -->
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
      // body.style.overflow = 'hidden';
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
    clickBurger() {
      this.isBurgerActive = !this.isBurgerActive;
      const body = document.querySelector('body');
      if (this.isBurgerActive) {
        body.style.overflow = 'hidden';
      }
      else {
        body.style.overflow = 'visible';
      }
      
    },
    clickMenu() {
      this.isBurgerActive = !this.isBurgerActive;
      const body = document.querySelector('body');
      body.style.overflow = 'visible';
      this.isMenuActive = true;
      this.$emit('close-burger');
    }
  }
}
</script>

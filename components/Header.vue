<template>
  <div>
  <div class="container container_header bg-body">

    <header class="header color-dark link_button">

      <div class="logo" @click="openIndex()">
        <Nuxt-Link to="/"></Nuxt-Link>
      </div>
      
      <ul class="navbar">
        <li @click="openIndex()"><Nuxt-Link :to="{path:'/', hash:'#favorite_coffee'}" href="#favorite_coffee" class="color-dark">Favorite coffee</Nuxt-Link></li> 
        <li @click="openIndex()"><Nuxt-Link :to="{path:'/', hash:'#about'}" href="#about" class="color-dark">About</Nuxt-Link></li>
        <li @click="openIndex()"><Nuxt-Link :to="{path:'/', hash:'#mobile-app'}" href="#mobile-app" class="color-dark">Mobile app</Nuxt-Link></li>
        <li @click="openIndex()"><a href="#footer" class="color-dark">Contact us</a></li>
      </ul>
      
      <div class="menu" @click="clickMenu()" >
        <Nuxt-Link to="/menu" class="btn menu_item coffee link_button color-dark" :class="{'active' : this.pathIsMenu}" >
          <div class="menu_item-main">
            <div class="menu_item-main-word">Menu</div>
            <div class="menu_item-main-icon"></div>
          </div>  
          <div class="line_down-hover"></div>
        </Nuxt-Link>
      </div>

      <!-- media 768px -->
      <button @click="clickBurger()" class="btn btn_burger" :class="{'active' : this.isBurgerActive}">
        <div class="btn_burger-line line-1"></div>
        <div class="btn_burger-line line-2"></div>
      </button>

    </header>
  </div>
  <Burger class="burger_menu" :class="{'active' : this.isBurgerActive}" :is-burger-active-prop="isBurgerActive" @open-index="openIndex()" @open-menu="openMenu()"/>
</div>
</template>

<script>
import Burger from '/components/Burger.vue';
export default {
  name: "HeaderComponent",
  props: ['isBurgerActiveProp', 'pathIsMenuProp'],
  mounted() {
      this.pathIsMenu = window.location.pathname == '/menu';
    },
  data() {
    return {
      isBurgerActive : this.isBurgerActiveProp,
      isMenuActive: false,
      pathIsMenu: false
    }
  },

  // computed: {
  //   pathIsMenu() {
  //     return window.location.pathname == '/menu';
  //   },
  // },
  methods: {
    clickMenu() {
      // document.location.reload();
      this.isMenuActive = true;
      this.$emit('click-menu', this.isMenuActive);
    },
    clickBurger() {
      this.isBurgerActive = !this.isBurgerActive;
      this.$emit('click-burger', this.isBurgerActive);
    },
    openIndex() {
      this.isBurgerActive = false;
      this.isMenuActive = false;
      this.pathIsMenu = false;
      this.$emit('close-burger', this.isBurgerActive);
    },
    openMenu() {
      this.isBurgerActive = false;
      this.isMenuActive = true;
      this.$emit('close-burger', this.isBurgerActive);
    }
  }
}
</script>
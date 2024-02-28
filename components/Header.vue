<template>
  <div class="container">

    <header class="header color-dark link_button">

      <Nuxt-Link to="/" class="logo"></Nuxt-Link>
      <ul class="navbar">
        <li><a href="#favorite_coffee" class="color-dark">Favorite coffee</a></li> 
        <li><a href="#about" class="color-dark">About</a></li>
        <li><a href="#mobile-app" class="color-dark">Mobile app</a></li>
        <li><a href="#footer" class="color-dark">Contact us</a></li>
      </ul>
      
      <div class="menu" @click="clickMenu()" >
        <Nuxt-Link to="/menu" class="btn menu_item coffee link_button color-dark" :class="{'active' : isMenuActive}" >
          <div class="menu_item-main">
            <div class="menu_item-main-word">Menu</div>
            <div class="menu_item-main-icon"></div>
          </div>  
          <div class="line_down-hover" ></div>
        </Nuxt-Link>
      </div>

      <!-- media 768px -->
      <button class="btn btn_burger" :class="{'active' : isBurgerActive}" @click="$emit('click-burger'); isBurgerActive=!isBurgerActive">
        <div class="btn_burger-line line-1"></div>
        <div class="btn_burger-line line-2"></div>
      </button>

    </header>
  </div>
</template>

<script>
export default {
  name: "HeaderComponent",
  created: function() {
    this.$parent.$on('close-burger', this.closeBurger);
  },
  
  data() {
    return {
      isMenuActive: false,
      isBurgerActive: false
    }
  },
  methods: {
    clickMenu() {
      this.isMenuActive = !this.isMenuActive;
      this.$emit('click-menu', this.isMenuActive);
    },
    closeBurger() {
      this.isBurgerActive = false;
    }
  }
}
</script>
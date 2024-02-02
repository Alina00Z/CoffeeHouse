<template>
  <div class="container">

    <header class="header color-dark link_button">

      <a href="#" class="logo"></a>
      <ul class="navbar">
        <li><a href="#" class="color-dark">Favorite coffee</a></li> 
        <li><a href="#" class="color-dark">About</a></li>
        <li><a href="#" class="color-dark">Mobile app</a></li>
        <li><a href="#" class="color-dark">Contact us</a></li>
      </ul>
      <button class="btn menu_item link_button" :class="{'active' : isMenuActive}" @click="clickCoffeeMenu()">
        <div class="menu_item-main">
          <div class="menu_item-main-word">Menu</div>
          <div class="menu_item-main-icon"></div>
        </div>  
        <div class="line_down-hover"></div>
      </button>

    </header>
  </div>
</template>

<script>
export default {
  name: "HeaderComponent",

  data() {
    return {
      isMenuActive: false
    }
  },
  methods: {
    clickCoffeeMenu() {
      this.isMenuActive = !this.isMenuActive;
      this.$emit('click-coffee-menu', this.isMenuActive);
    }
  }
}
</script>
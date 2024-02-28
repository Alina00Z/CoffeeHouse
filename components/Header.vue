<template>
  <div class="container container_header bg-body">

    <header class="header color-dark link_button">

      <div class="logo" @click="openIndex()">
        <Nuxt-Link to="/" ></Nuxt-Link>
      </div>
      
      <ul class="navbar">
        <li @click="openIndex()"><Nuxt-Link :to="{path:'/', hash:'#favorite_coffee'}" href="#favorite_coffee" class="color-dark">Favorite coffee</Nuxt-Link></li> 
        <li @click="openIndex()"><Nuxt-Link :to="{path:'/', hash:'#about'}" href="#about" class="color-dark">About</Nuxt-Link></li>
        <li @click="openIndex()"><Nuxt-Link :to="{path:'/', hash:'#mobile-app'}" href="#mobile-app" class="color-dark">Mobile app</Nuxt-Link></li>
        <li @click="openIndex()"><a href="#footer" class="color-dark">Contact us</a></li>
      </ul>
      
      <div class="menu" @click="clickMenu()" >
        <Nuxt-Link to="/menu" class="btn menu_item coffee link_button color-dark" :class="{'active' : isMenuActive}" >
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
</template>

<script>
export default {
  name: "HeaderComponent",
  created: function() {
    // this.$parent.$on('close-burger', this.closeBurger);
  },
  props: ['isBurgerActiveProp'],
  data() {
    return {
      isBurgerActive : this.isBurgerActiveProp,
      isMenuActive: false,
    }
  },
  methods: {
    clickMenu() {
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
      this.$emit('close-burger', this.isBurgerActive);
    }
  }
}
</script>
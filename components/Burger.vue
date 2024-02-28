<template>

<div class="burger_menu color-dark burger-link">
  <ul class="burger_menu-navbar">

    <li class="btn menu_item" @click="openMenu()">
      <Nuxt-Link :to="{ path: '/',hash:'#favorite_coffee'}">
        <div class="menu_item-main">
          <div class="menu_item-main-word">Favorite coffee</div>
        </div>  
        <div class="line_down-hover"></div>
      </Nuxt-Link>
    </li>

    <li class="btn menu_item" @click="openMenu()">
      <Nuxt-Link :to="{ path: '/',hash:'#about'}">
        <div class="menu_item-main">
          <div class="menu_item-main-word">About</div>
        </div>  
        <div class="line_down-hover"></div>
      </Nuxt-Link>
    </li>

    <li class="btn menu_item" @click="openMenu()">
      <Nuxt-Link :to="{ path: '/',hash:'#mobile-app'}">
        <div class="menu_item-main">
          <div class="menu_item-main-word">Mobile app</div>
        </div>  
        <div class="line_down-hover"></div>
      </Nuxt-Link>
    </li>

    <li class="btn menu_item" @click="openMenu()">
      <Nuxt-Link :to="{ path: '/',hash:'#footer_for_scroll'}">
        <div class="menu_item-main">
          <div class="menu_item-main-word">Contact us</div>
        </div>  
        <div class="line_down-hover"></div>
      </Nuxt-Link>
    </li>

  </ul>
  <li class="btn menu_item" @click="openMenu()">
    <Nuxt-Link to="/menu">
      <div class="menu_item-main">
        <div class="menu_item-main-word">Menu</div>
        <div class="menu_item-main-icon"></div>
      </div>  
      <div class="line_down-hover"></div>
    </Nuxt-Link>
    </li>
</div>

</template>

<script>
export default {
  name: 'BurgerComponent',
  data() {
    return {
    }
  },
  methods: {
    openMenu() {
      this.$emit('open-menu');
    }
  }
}
</script>
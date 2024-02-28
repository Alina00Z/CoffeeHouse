<template>

  <div class="container">
    <div class="window_coffee">
    
      <div class="window_coffee-offer">
        <h1 class="heading-2 color-dark">Behind each of our cups hides an <span class="accent color-accent">amazing surprise</span></h1>
        
        <ul class="tabs link_button">
          <li ref="coffee_tab" class="tab_item active" @click="clickCoffee()">
            <!-- ☕ -->
            <div class="tab_item-icon">
              <div class="circle"></div>
              <div class="emoji">&#9749;</div>
            </div>
            <div class="tab_item-word">Coffee</div>
          </li>
          <li ref="tea_tab" class="tab_item" @click="clickTea()">
            <!-- 🫖  &#129750;-->
            <div class="tab_item-icon">
              <div class="circle"></div>
              <div class="emoji">&#129750;</div>
            </div>
            <div class="tab_item-word">Tea</div>
          </li>
          <li ref="dessert_tab" class="tab_item" @click="clickDessert()">
            <!-- 🍰 &#127856;-->
            <div class="tab_item-icon">
              <div class="circle"></div>
              <div class="emoji">&#127856;</div>
            </div>
            <div class="tab_item-word">Dessert</div>
          </li>
        </ul>
      </div>
  
      <div v-if="tabsState[0].active" class="window-coffee-grid">
        <coffee-menu-card @click-card="$nuxt.$emit('click-card', $event)" v-for="(card,i) in cards_coffee" :key="i" :type="'coffee'" :name="card.name" :info="card.info" :price="card.price"/>
      </div>
      <div v-if="tabsState[1].active" class="window-coffee-grid">
        <coffee-menu-card @click-card="$nuxt.$emit('click-card', $event)" v-for="(card,i) in cards_tea" :key="i" :type="'tea'" :name="card.name" :info="card.info" :price="card.price"/>
      </div>
      <div v-if="tabsState[2].active" class="window-coffee-grid">
        <coffee-menu-card @click-card="$nuxt.$emit('click-card', $event)" v-for="(card,i) in cards_dessert" :key="i" :type="'dessert'" :name="card.name" :info="card.info" :price="card.price"/>
      </div>
  
    </div>
  </div>
  
  </template>
  <script>
  import CoffeeMenuCard from '../components/CoffeeMenuCard.vue'
  export default {
    name: 'MenuPage',
    layout: 'default',
    components: {
      CoffeeMenuCard,
    },
    
    
    data() {
      return {
        tabsState: [
          { name: 'coffee', active: true},
          { name: 'tea', active: false},
          { name: 'dessert', active: false}
        ],
        cards_coffee: [
          {name: 'Irish coffee', info: 'Fragrant black coffee with Jameson Irish whiskey and whipped milk', price: '$7.00'},
          {name: 'Kahlua coffee', info: 'Classic coffee with milk and Kahlua liqueur under a cap of frothed milk', price: '$7.00'},
          {name: 'Honey raf', info: 'Espresso with frothed milk, cream and aromatic honey', price: '$5.50'},
          {name: 'Ice cappuccino', info: 'Cappuccino with soft thick foam in summer version with ice', price: '$5.00'},
          {name: 'Espresso', info: 'Classic black coffee', price: '$4.50'},
          {name: 'Latte', info: 'Espresso coffee with the addition of steamed milk and dense milk foam', price: '$5.50'},
          {name: 'Latte macchiato', info: 'Espresso with frothed milk and chocolate', price: '$5.50'},
          {name: 'Coffee with cognac', info: 'Fragrant black coffee with cognac and whipped cream', price: '$6.50'}
        ],
        cards_tea: [
          {name: 'Moroccan', info: 'Fragrant black tea with the addition of tangerine, cinnamon, honey, lemon and mint', price: '$4.50'},
          {name: 'Ginger', info: 'Original black tea with fresh ginger, lemon and honey', price: '$5.00'},
          {name: 'Cranberry', info: 'Invigorating black tea with cranberry and honey', price: '$5.00'},
          {name: 'Sea buckthorn', info: 'Toning sweet black tea with sea buckthorn, fresh thyme and cinnamon', price: '$5.50'}
        ],
        cards_dessert: [
          {name: 'Marble cheesecake', info: 'Philadelphia cheese with lemon zest on a light sponge cake and red currant jam', price: '$3.50'},
          {name: 'Red velvet', info: 'Layer cake with cream cheese frosting', price: '$4.00'},
          {name: 'Cheesecakes', info: 'Soft cottage cheese pancakes with sour cream and fresh berries and sprinkled with powdered sugar', price: '$4.50'},
          {name: 'Creme brulee', info: 'Delicate creamy dessert in a caramel basket with wild berries', price: '$4.00'},
          {name: 'Pancakes', info: 'Tender pancakes with strawberry jam and fresh strawberries', price: '$4.50'},
          {name: 'Honey cake', info: 'Classic honey cake with delicate custard', price: '$4.50'},
          {name: 'Chocolate cake', info: 'Cake with hot chocolate filling and nuts with dried apricots', price: '$5.50'},
          {name: 'Black forest', info: 'A combination of thin sponge cake with cherry jam and light chocolate mousse', price: '$6.50'}
        ],
        card_selected : null
      }
    },
    computed: {
      
    },
    methods: {
      clickCoffee() {
        this.$refs.tea_tab.classList.remove('active');
        this.tabsState[1].active = false;
        this.$refs.dessert_tab.classList.remove('active');
        this.tabsState[2].active = false;
        this.$refs.coffee_tab.classList.add('active');
        this.tabsState[0].active = true;
  
      },
      clickTea() {
        this.$refs.coffee_tab.classList.remove('active');
        this.tabsState[0].active = false;
        this.$refs.dessert_tab.classList.remove('active');
        this.tabsState[2].active = false;
        this.$refs.tea_tab.classList.add('active');
        this.tabsState[1].active = true;
      },
      clickDessert() {
        this.$refs.coffee_tab.classList.remove('active');
        this.tabsState[0].active = false;
        this.$refs.tea_tab.classList.remove('active');
        this.tabsState[1].active = false;
        this.$refs.dessert_tab.classList.add('active');
        this.tabsState[2].active = true;
      }
    }
  }
  </script>
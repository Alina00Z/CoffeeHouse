<template>
  <div class="modal_card bg-body color-dark">

  <img class="modal_card-image" width="310px" height="310px" :src="require(`~/assets/${card.type}/${card.name}.png`)"/>
  
  <div class="modal_card-description">

    <div class="modal_card-description-title">
      <h3 class="heading-3">{{ card.name }}</h3> 
      <p class="font-medium">{{ card.info }}</p>
    </div>

    <div> Size
      <ul class="tabs link_button modal_tabs">
          <li class="tab_item active">
            <div class="tab_item-icon">
              <div class="circle"></div>
              <div class="emoji">S</div>
            </div>
            <div class="tab_item-word">200 ml</div>
          </li>
          <li class="tab_item">
            <div class="tab_item-icon">
              <div class="circle"></div>
              <div class="emoji">S</div>
            </div>
            <div class="tab_item-word">300 ml</div>
          </li>
          <li class="tab_item">
            <div class="tab_item-icon">
              <div class="circle"></div>
              <div class="emoji">S</div>
            </div>
            <div class="tab_item-word">400 ml</div>
          </li>
      </ul>
    </div>

    <div> Additives
      <ul class="tabs link_button modal_tabs">
          <li class="tab_item active">
            <div class="tab_item-icon">
              <div class="circle"></div>
              <div class="emoji">1</div>
            </div>
            <div class="tab_item-word">Sugar</div>
          </li>
          <li class="tab_item">
            <div class="tab_item-icon">
              <div class="circle"></div>
              <div class="emoji">2</div>
            </div>
            <div class="tab_item-word">Cinnamon</div>
          </li>
          <li class="tab_item">
            <div class="tab_item-icon">
              <div class="circle"></div>
              <div class="emoji">3</div>
            </div>
            <div class="tab_item-word">Syrup</div>
          </li>
      </ul>
    </div>
    <div class="modal_card-description-total heading-3">
      <div>Total:</div>
      <div>$7.00</div>
    </div>
    <div class="modal_card-description-alert font-caption">
      <img src="~/assets/info-empty.svg">
      <p>The cost is not final. Download our mobile app to see the final price and place your order. Earn loyalty points and enjoy your favorite coffee with up to 20% discount.</p>
    </div>

    <button class="btn link_button button_secondary" @click="$emit('close-modal')">
      Close
    </button>
    


  </div>
  


  </div>  
</template>

<style>
.modal_card-description-alert {
  border-top: 1px solid #C1B6AD;

  display: flex;
  flex-direction: row;
  padding: 12px 0px;
}
.modal_card-description-alert > img {
  height: 16px;
  margin-right: 8px;
}

.modal_card-image {
  border-radius: 40px;
}
.modal_card {
  position: fixed;
  z-index: 20;
  width: 800px;
  height: 504px;
  
  /* 1 var */
  top: 50%; 
  left: 50%;
  transform: translate(-50%, -50%);

  /* 2 var */
  /* margin-top: -252px;
  left: 50%; 
  margin-left: -400px;  */

  border-radius: 40px;
  opacity: 0%;
  animation: appear_modal-opacity 0.6s ease-in-out 0.8s forwards;

  padding: 16px;

  display: flex;
  flex-direction: row;
} 
.modal_card-description {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 100%;
  padding-left: 20px;
}
.modal_tabs {
  margin-top: 8px;
}
.modal_tabs .tab_item:not(:last-child) {
  margin-right: 8px;
}
.modal_card-description-title > h3 {
  margin-bottom: 12px;
}
@keyframes appear_modal-opacity {
  0% {
    opacity: 0%
  }
  100% {
   opacity: 100%;
  }
}
/* @keyframes appear_modal-top {
  0% {
  }
  100% {
    transform: translateY(100%);
  }
} */

.modal_card-description-total {
  display: flex;
  justify-content: space-between;
}

@media (max-width: 768px) {
  .modal_card {
    width: 656px;
    height: 594px;
    /* margin-left: -328px; */
  }
  .modal_card .tab_item:last-child {
    margin-top: 8px;
  }
  .window_coffee-offer .tab_item:not(:last-child) {
    margin-right: 8px;
  }
}
@media (max-width:670px) {
  .modal_card {
    width: 342px;
    height: 626px;
    /* margin-left: -171px; */
  }
  .modal_card > img {
    display: none;
  }
  .modal_card-description {
    padding: 0px;
  }
}
@media (max-width: 380px) {
  
}

</style>
<script>
export default {
  props: {
    card: {
      type: Object
    }
  },
  data() {
    return {
    }
  }
}
</script>
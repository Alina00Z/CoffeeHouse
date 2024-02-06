<template>
<div class="slider">
  <div class="slider-main">

    <button class="btn btn-icon-dark left" @click="previousSlider()">
      <svg width="60" height="60" viewBox="0 0 60 60" fill="none" xmlns="http://www.w3.org/2000/svg">
      <rect x="0.5" y="0.5" width="59" height="59" rx="29.5" stroke="#665F55"/>
      <path d="M36.5 30H24M24 30L30 24M24 30L30 36" stroke="#403F3D" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </button>

      <div class="slider_window">

        <div ref="slider_track" class="slider_track active-1">
          <div ref="slide" class="slide color-dark">
            <img src="~/assets/coffee-slider-1.png">
            <div class="heading-3 name">S'mores Frappuccino</div>
            <p class="font-medium info">This new drink takes an espresso and mixes it with brown sugar and cinnamon before being topped with oat milk.</p>
            <p class="heading-3 price">$5.50</p>
          </div>
          <div ref="slide" class="slide">
            <img src="~/assets/coffee-slider-2.png">
            <div class="heading-3 name">Caramel Macchiato</div>
            <p class="font-medium info">Fragrant and unique classic espresso with rich caramel-peanut syrup, with cream under whipped thick foam.</p>
            <p class="heading-3 price">$5.00</p>
          </div>
          <div ref="slide" class="slide">
            <img src="~/assets/coffee-slider-3.png">
            <div class="heading-3 name">Ice coffee</div>
            <p class="font-medium info">A popular summer drink that tones and invigorates. Prepared from coffee, milk and ice.</p>
            <p class="heading-3 price">$4.50</p>
          </div>
        </div>

      </div>

      <button class="btn btn-icon-dark right" @click="nextSlider()">
        <svg width="60" height="60" viewBox="0 0 60 60" fill="none" xmlns="http://www.w3.org/2000/svg">
        <rect x="0.5" y="0.5" width="59" height="59" rx="29.5" stroke="#665F55"/>
        <path d="M36.5 30H24M24 30L30 24M24 30L30 36" stroke="#403F3D" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </button>

  </div>

  <div class="slider-controls">

    <div class="btn control active"></div>
    <div class="btn control"></div>
    <div class="btn control"></div>
    
  </div>

</div>
</template>

<style>
.slider {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: fit-content;
  margin: 0 auto;
}
.slider-main {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;

  /* user-select: none;
  touch-action: pan-y; */
}
.slider_track {
  display: flex;
  flex-direction: row;

  transition: margin-left 0.3s ease-in-out;
}
.slider_window {
  overflow: hidden;
  width: 480px;
  height: 640px;
}
.slider_window.grab {
  cursor: grab;
}
.slider_window.grabbing {
  cursor: grabbing;
}
.slide {
  width: 480px;
  height: 100%;
  flex-shrink: 0;

  display: flex;
  flex-direction: column;
  align-items: center;
}
.slide p {
  text-align: center;
}
.slide .name, .slide .info  {
  margin-bottom: 16px;
}
.slide img {
  /* pointer-events: none; */
  width: 100%;
  height: 480px;
  object-fit: cover;
  margin-bottom: 20px;
}
.control {
  width: 40px;
  height: 4px;
  background-color: #C1B6AD;
}
.control.active {
  background-color: #665F55;
}
.slider_track.active-1 {
  margin: 0px;
}
.slider_track.active-2 {
  margin-left: -480px;
}
.slider_track.active-3 {
  margin-left: -960px;
}
@media (max-width:675px) {
  .slider-main {
    height: 532px;
  }
  .slider_window {
    width: 348px;
    height: 532px;
  }
  .slide {
    width: 348px;
  }
  .slide img {
    height: 348px;
  }
  .slider_track.active-1 {
  margin: 0px;
}
.slider_track.active-2 {
  margin-left: -348px;
}
.slider_track.active-3 {
  margin-left: -696px;
}
}
</style>

<script>

export default {
  name: 'Slider',
  data() {
    return {
      number_active_slider: 1,
      number_previous_slider: 3,
      number_next_slider: 2,
      count_sliders: 3
    }
  },
  computed: {
    getNextSlider() { 
      const x = (this.number_active_slider + 1) % (this.count_sliders + 1); //  % 4
      if (x == 0) return 1;
      return x
    },
    getPreviousSlider() { 
      if (this.number_active_slider - 1 == 0) return 3;
      else return this.number_active_slider - 1;
    },
  },
  methods: {
    showSlider() {
      const controls = document.querySelectorAll('.control');
      this.$refs.slider_track.classList.remove(`active-${this.number_previous_slider}`); // 3
      controls[this.number_previous_slider-1].classList.remove('active');
      this.$refs.slider_track.classList.add(`active-${this.number_active_slider}`);
      controls[this.number_active_slider-1].classList.add('active');
    },
    previousSlider() {
      this.number_previous_slider = this.number_active_slider; 
      this.number_active_slider = this.getPreviousSlider; 
      this.number_next_slider = this.getNextSlider;
      this.showSlider();
    },
    nextSlider() {
      this.number_previous_slider = this.number_active_slider;
      this.number_active_slider = this.getNextSlider; 
      this.number_next_slider = this.getNextSlider;
      this.showSlider();
    }
  }
}

</script>
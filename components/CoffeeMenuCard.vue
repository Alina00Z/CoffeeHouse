<template>
<div class="card color-dark" @click="$emit('click-card', [type, name, info, price])">
  
  <div class="card-box_image">
    <img class="card-image" :src="require(`~/assets/${type}/${name}.png`)"/>
  </div>
  <div class="card-info">
    <h3 class="heading-3">{{ name }}</h3>
    <p class="font-medium">{{ info }}</p>
    <p class="heading-3">{{ price }}</p>
  </div>

</div>
</template>
<style>
.card {
  width: 310px;
  height: 506px;
  border-radius: 40px;
  border: 1px solid #C1B6AD;
  cursor: pointer;
}
.card-box_image {
  width: 308px;
  height: 309px;
  overflow: hidden;
  border-radius: 40px;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.card-image {
  border-radius: 40px;
  object-fit: cover;
  transition: transform 0.3s ease;
}
.card:hover .card-image{
  transform: scale(0.91);
}
.card-info {
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.card-info > h3, .card-info > p {
  margin-bottom: 12px;
}
</style>

<script>
export default {
  name: "CoffeeMenuCard",
  props: {
    type: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    info: {
      type: String,
      required: false,
      default: ''
    },
    price: {
      type: String,
      required: false,
      default: '-'
    },
  }
}

</script>
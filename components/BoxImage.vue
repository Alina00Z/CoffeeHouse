<template>

<div class="box_image">
    <img class="image" :src="pathImage">
</div>

</template>

<style>
.box_image {
  width: 660px;
  height: 660px;
  overflow: hidden;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  cursor: pointer;
  border-radius: 40px;
}
.box_image > img {
  transition: transform 0.3s ease;
}
.box_image:hover .image {
  transform: scale(0.91);
}
</style>
<script>
export default {
  name: 'BoxImage',
  props: {
    pathImage : {
      type: String,
      required: true
    },
  },
}
</script>
<template>
  <div>
    <img class="image" :src="image" />
    <h5>{{name}}</h5>
    <h4>Rp. {{price}}</h4>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: ['name', 'image', 'price']
}
</script>

<style scoped>
.image {
  width: 220px;
  height: 180px;
  border-radius: 10px 10px 0px 0px;
}
div{
  margin: 10px;
}

</style>

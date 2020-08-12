<template>
  <header class="row justify-content-between">
          <img class="icon" src="../../assets/menu.png" />
          <h2>Food Items</h2>
          <img class="icon" src="../../assets/magnifying-glass.png" />
</header>
</template>

<script>
export default {
  name: 'Home'

}
</script>

<style scoped>
/* Header */

header {
  padding: 20px;
  background: #ffffff;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.25);
}

header.row {
  justify-content: space-between;
}

header h2,
aside .cart h2 {
  font-size: 30px;
  line-height: 39px;
  color: #000000;
}

.icon {
  width: 35px;
  height: 35px;
  margin-left: 5px;
}
</style>

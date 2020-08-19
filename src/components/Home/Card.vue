<template>
  <div v-show="active">
    <div class="select">
      <img class="image" :src="image" @click="addToCart" />
      <div v-show="select" class="tick"></div>
    </div>
    <h5>{{name}}</h5>
    <h5>Rp. {{price}}</h5>
    <!-- <h5>{{id}}</h5> -->
    <!-- <h5>{{select}}</h5>
    <h5>{{total}}</h5> -->
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: ['name', 'image', 'price', 'id'],
  data () {
    return {
      select: false,
      active: true
    }
  },
  mounted () {
    // this.selectItem = false
  },
  computed: {
    total: function () {
      let totalPrice = 0
      totalPrice += this.price
      return totalPrice
    }
  },
  methods: {
    addToCart () {
      if (this.select === false) {
        this.$emit('addToCart', {
          count: 1,
          empty: false,
          name: this.name,
          image: this.image,
          price: this.price,
          id: this.id,
          quality: 1,
          plus: this.price
        })
      } else {
        this.$emit('addToCart', {
          count: -1,
          empty: false,
          name: this.name,
          image: this.image,
          price: this.price,
          id: this.id
          // selectItem: this.selectItem
        })
      }

      if (this.select === true) {
        this.select = false
      } else {
        this.select = true
      }
    }
  }
}
</script>

<style scoped>
.select {
  margin-bottom: 5px;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* .select .image {
  filter: brightness(50%);
} */

.tick {
  position: absolute;
  width: 40px;
  height: 40px;
  background-image: url("../../assets/tick.png");
  background-size: 40px;
}

h4,
h5,
button {
  font-family: Airbnb Cereal App;
}

.image {
  width: 220px;
  height: 180px;
  border-radius: 10px 10px 0px 0px;
}
div {
  margin: 10px;
}
@media (max-width: 768px) {
  .image {
    width: 350px;
    height: 220px;
    border-radius: 10px 10px 0px 0px;
  }
  header,
  aside .cart {
    height: 50px;
  }
  header h2,
  aside .cart h2 {
    font-size: 20px;
    line-height: 20px;
  }
  main {
    height: 310px;
  }
  article h6 {
    font-size: 10px;
  }
  article h3 {
    font-size: 13px;
  }
  aside h3 {
    font-size: 12px;
    line-height: 20px;
  }
  aside h4 {
    /* font-size: 8px; */
    line-height: 10px;
  }
  aside .list .item h3 {
    font-size: 10px;
  }
  aside .list .price h4 {
    font-size: 10px;
  }
  aside .scroll {
    overflow-y: scroll;
    height: 300px;
  }
  aside .scroll::-webkit-scrollbar {
    display: none;
  }
  aside .btm .checkout {
    margin-top: 10px;
  }
  aside .btm .checkout {
    padding: 5px;
  }
  aside .btm .cancel {
    padding: 10px;
  }
}

@media (max-width: 576px) {
  .icon {
    width: 15px;
    height: 15px;
  }
  .image {
    width: 180px;
    height: 150px;
    border-radius: 10px 10px 0px 0px;
  }
  main {
    height: 600px;
  }
  main .menu .row {
    flex-direction: column;
  }
  article h6 {
    font-size: 20px;
  }
  aside .scroll {
    overflow-y: scroll;
    height: 600px;
  }
  aside .scroll::-webkit-scrollbar {
    display: none;
  }
  aside .list h3 {
    font-size: 12px;
    flex-direction: column;
  }
  aside .list h4 {
    flex-direction: column;
    font-size: 12px;
    padding-top: 5px;
  }
  aside .list .select {
    justify-content: center;
    padding: 10px;
    padding-top: 0;
  }
  aside .list .price {
    flex-direction: column;
  }
  aside .btm {
    padding: 5px;
  }
  aside .btm h3 {
    font-size: 11px;
  }
  aside .btm p {
    font-size: 10px;
  }
}
</style>

<template>
  <div>
    <div class="cos-container">
      <div class="container-fluid">
        <div class="row">
          <div class="col-md-9 col-sm-9 main-bar">
            <Header />
            <div class="row">
              <Navbar />
              <router-view v-on:updateCart="addToCart($event)" />
            </div>
          </div>
          <aside class="col-md-3 p-md-0 col-sm-3 p-sm-0">
            <Cart :count="count" v-on:toCart="addItemCart($event)" />
            <Empty v-if="empty" />
            <div v-else class="scroll">
              <div v-for="Product in cartProducts" :key="Product.id">
                <Checkout
                  :name="Product.name"
                  :image="Product.image"
                  :price="Product.price"
                  v-on:plus="totalPrice($event)"
                />
              </div>
              <CheckoutPay
              :name="cartProducts.name"
              :image="cartProducts.image"
              :price="cartProducts.price"
              v-on:cancel="cancelCart($event)"
              />
            </div>
          </aside>
        </div>
        <Add />
        <CheckModal />
      </div>
    </div>
  </div>
</template>

<script>
import Header from '../../components/Home/Header'
import Navbar from '../../components/Home/Navbar'
import Cart from '../../components/Home/Cart'
import Empty from '../../components/Home/Empty'
import Checkout from '../../components/Home/checkout'
import Add from '../../components/Home/Modal-Add'
import CheckModal from '../../components/Home/Modal-Checkout'
import CheckoutPay from '../../components/Home/checkoutPay'

export default {
  name: 'Main',
  components: {
    Header,
    Navbar,
    Cart,
    Empty,
    Checkout,
    CheckoutPay,
    Add,
    CheckModal
  },
  data () {
    return {
      empty: true,
      count: 0,
      cartProducts: [],
      totals: []
    }
  },
  methods: {
    addToCart (addToCart) {
      this.count = this.count + addToCart.count
      this.empty = addToCart.empty
      if (addToCart.name !== this.cartProducts.name) {
        this.cartProducts.push(addToCart)
      }
    },
    // addItemCart (addItemCart) {
    //   this.empty = addItemCart
    // },
    totalPrice (totalPrice) {
      this.total = totalPrice
    },
    cancelCart (cancelCart) {
      this.empty = cancelCart.empty
      this.count = cancelCart.count
      this.cartProducts = []
    }
  }
}
</script>

<style scoped>
.cos-container {
  min-height: 500px;
}

.scroll {
  height: 610px;
  overflow-y: scroll;
}

.scroll::-webkit-scrollbar {
  display: none;
}

@media (max-width: 768px) {
  .cos-container {
    min-height: 310px;
  }
  .scroll {
    height: 310px;
  }
}
</style>

<template>
  <!-- <div>
        <h2>halaman Home</h2>
        <button @click="linkHistory">ke history</button>
  </div>-->
  <div class="container-fluid">
    <div class="row">
      <div class="col-md-9 col-sm-9 main-bar">
        <Header />
        <div class="row">
          <Navbar />
          <main class="col-md-11 col-sm-11">
            <div class="row justify-content-center">
              <article v-for="product in products" :key="product.id">
              <Card :name="product.name" :image="product.image" :price="product.price" v-on:toggle-event="clikBtn" />
              </article>
            </div>
          </main>
        </div>
      </div>
      <aside class="col-md-3 p-md-0 col-sm-3 p-sm-0">
        <div class="row cart m-md-0 m-sm-0 justify-content-center">
          <h2>
            Cart
            <span class="count">0</span>
          </h2>
        </div>
        <div class="row list m-md-0 m-sm-0">
          <div class="col">
            <div class="row p-md-3 p-sm-1 d-flex justify-content-center">
              <img class="image-empty" src="../../../assets/food-and-restaurant.png" />
            </div>
            <div class="row d-flex justify-content-center">
              <h3>Your cart is empty</h3>
            </div>
            <div class="row d-flex justify-content-center">
              <h4>Please add some items from the menu</h4>
            </div>
          </div>
        </div>
      </aside>
    </div>
  </div>
</template>

<script>
import Header from '../../../components/_base/Header'
import Navbar from '../../..//components/_base/Navbar'
import Card from '../../../components/_base/Card'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    Header,
    Navbar,
    Card
  },
  data () {
    return {
      products: []
    }
  },
  methods: {
    linkHistory () {
      this.$router.push({
        name: 'history',
        params: { id: 5, name: 'risano', email: 'risa@gamil.com' },
        query: { search: 'akbar' }
      })
    },
    getData () {
      axios.get('http://localhost:4000/api/v1/products')
        .then((res) => {
          this.products = res.data.result
        })
    }
  },
  mounted () {
    this.getData()
  }
}
</script>

<style scoped>
/* Background Check */

.red {
  background-color: red;
}

.blue {
  background-color: blue;
}

.yellow {
  background-color: yellow;
}

.green {
  background-color: green;
}

.orange {
  background-color: orangered;
}

.black {
  background-color: black;
}

.white {
  background-color: white;
}

/* End-Background Check */

.image-empty {
  width: 250px;
  height: 270px;
}

h2,
h3,
h4,
button {
  font-family: Airbnb Cereal App;
}

/* Main */

main {
  height: 610px;
  background: rgba(190, 195, 202, 0.3);
  flex-wrap: wrap;
  overflow-y: scroll;
}

main::-webkit-scrollbar {
  display: none;
}

main .menu {
  width: 100%;
}

.menu .row {
  justify-content: center;
}

/* Article */

article {
  padding: 20px;
}

article .select {
  margin-bottom: 5px;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* article h6.text {
  font-size: 18px;
} */

article .select .image {
  /* opacity: 0.8; */
  filter: brightness(50%);
}

.tick {
  position: absolute;
  width: 40px;
  height: 40px;
  background-image: url("../../../assets/tick.png");
  background-size: 40px;
}

/* Aside */

aside {
  background: #ffffff;
  border: 1px solid #cecece;
}

aside .cart {
  box-shadow: 0px 4px 1px rgba(0, 0, 0, 0.25);
  padding: 20px;
}

aside .cart .count {
  background: #57cad5;
  border-radius: 100%;
  padding-left: 5px;
  padding-right: 5px;
  font-size: 20px;
  line-height: 26px;
  color: #ffffff;
}

/* Aside List */

aside {
  width: 30%;
  background: #ffffff;
  border: 1px solid #cecece;
}

aside .row {
  justify-content: center;
}

aside .cart {
  box-shadow: 0px 4px 1px rgba(0, 0, 0, 0.25);
  padding: 20px;
}

aside .count {
  background: #57cad5;
  border-radius: 100%;
  padding-left: 5px;
  padding-right: 5px;
  font-size: 20px;
  line-height: 26px;
  color: #ffffff;
}

aside .list img {
  padding-top: 50px;
}

aside h2 {
  font-size: 30px;
  line-height: 40px;
}

aside h3 {
  font-size: 25px;
  line-height: 40px;
}

aside h4 {
  font-size: 12px;
  line-height: 25px;
  color: #cecece;
}

/* Modal */

.modal .modal-body h6 {
  height: 35px;
  padding-top: 5px;
}

.modal .modal-body input {
  background: #ffffff;
  border: 1px solid #cecece;
  box-sizing: border-box;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.25);
  border-radius: 5px;
  width: 100%;
  height: 35px;
}

.modal .modal-body input.price {
  width: 60%;
}

.modal .modal-body select .option {
  color: #cecece;
}

.modal .modal-body select {
  background: #ffffff;
  border: 1px solid #cecece;
  box-sizing: border-box;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.25);
  border-radius: 5px;
  width: 40%;
  height: 35px;
}

.modal .modal-body .btn {
  width: 440px;
  height: 60px;
  font-weight: bold;
  font-size: 30px;
  margin: auto;
  border-radius: 10px;
  border: 0;
}

.modal .modal-body .btn-primary {
  background-color: #57cad5;
  border-radius: 10px;
  width: 100px;
  height: 35px;
  font-size: 15px;
}

.modal .modal-body .btn-danger {
  background-color: #f24f8a;
  border-radius: 10px;
  width: 100px;
  height: 35px;
  font-size: 15px;
}

@media (max-width: 768px) {
  .icon {
    width: 20px;
    height: 20px;
  }
  .image {
    width: 100px;
    height: 80px;
    border-radius: 10px 10px 0px 0px;
  }
  .image-empty {
    width: 100px;
    height: 150px;
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
  article h4.text {
    font-size: 9px;
  }
  aside h3 {
    font-size: 12px;
    line-height: 20px;
  }
  aside h4 {
    font-size: 8px;
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

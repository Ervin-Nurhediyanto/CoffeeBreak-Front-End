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
    <div class="row yellow">
      <article class="row justify-content-center blue" v-for="product in products" :key="product.id">
        <Card class="red"
          :name="product.name"
          :image="product.image"
          :price="product.price"
          v-on:toggle-event="clikBtn"
        />
      </article>
      <article class="page row justify-content-between">
        <!-- <h4 class ="red" @click="prevPage">prev</h4>
        <h4 class ="green">page {{page}}</h4>
        <h4 class ="blue" @click="nextPage">next</h4> -->

          <button @click="prevPage" value="1">prev</button>
          <h4 class ="green">page {{page}}</h4>
          <button @click="nextPage" value="2">prev</button>
          <input :value='search'>
      </article>
      <article>
      <form @submit="formSubmit">
                        <strong>Name:</strong>
                        <input type="text" class="form-control" v-model="name">
                        <strong>Price:</strong>
                        <textarea class="form-control" v-model="price"></textarea>
                        <strong>Image:</strong>
                        <input type="text" class="form-control" v-model="image">
                        <strong>Category:</strong>
                        <input type="text" class="form-control" v-model="idCategory">
                        <button class="btn btn-success">Submit</button>
                        </form>
      </article>
    </div>
  </main>
        </div>
      </div>
      <Sidebar />
    </div>
  </div>
</template>

<script>
import Header from '../../../components/_base/Header'
import Navbar from '../../../components/_base/Navbar'
// import Product from '../../../components/_base/Product'
import Sidebar from '../../../components/_base/Sidebar'
import Card from '../../../components/_base/Card'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    Header,
    Navbar,
    // Product,
    Sidebar,
    Card
  },
  data () {
    return {
      products: [],
      page: '',
      search: '',
      name: '',
      price: '',
      image: '',
      idCategory: ''
    }
  },
  mounted () {
    this.getData()
  },
  methods: {
    linkHistory () {
      this.$router.push({
        name: 'history',
        params: { id: 5, name: 'risano', email: 'risa@gamil.com' },
        query: { search: 'akbar' }
      })
    },
    prevPage () {
      const prevPage = this.page - 1
      axios.get(`http://localhost:4000/api/v1/products/?page=${prevPage}`)
        .then((res) => {
          this.products = res.data.result
          this.page = res.data.page
        })
    },
    // thisPage () {
    //   this.$router.push({
    //     name: 'history',
    //     params: { id: 5, name: 'risano', email: 'risa@gamil.com' },
    //     query: { search: 'akbar' }
    //   })
    // },
    nextPage () {
      let nextPage = this.page
      nextPage += 1
      this.$router.push({
        name: 'home',
        query: { page: nextPage }
      })

      // axios.get(`http://localhost:4000/api/v1/products/?page=${nextPage}`)
      //   .then((res) => {
      //     this.products = res.data.result
      //     this.page = res.data.page
      //   })
    },
    getData () {
      axios.get('http://localhost:4000/api/v1/products')
        .then((res) => {
          this.products = res.data.result
          // this.page = res.data.page
        })
    },
    postData () {
      formSubmit(e) {
                e.preventDefault();
                let currentObj = this;
                this.axios.post('http://localhost:4000/api/v1/products', {
                    name: this.name,
                    description: this.description
                })
                .then(function (response) {
                    currentObj.output = response.data;
                })
                .catch(function (error) {
                    currentObj.output = error;
                })
            }
    }
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
h2,
h3,
h4,
button {
  font-family: Airbnb Cereal App;
}
/* Article */

article {
  padding: 20px;
}

article.page {
  width: 100%;
}

article .select {
  margin-bottom: 5px;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
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
main div {
    padding: 0;
}
article {
    margin:0;
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

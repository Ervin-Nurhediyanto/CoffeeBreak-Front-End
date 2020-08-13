<template>
  <main class="col-md-11 col-sm-11 red">
    <div class="row justify-content-center yellow">
      <article v-for="product in products" :key="product.id" class="blue">
        <Card
          :name="product.name"
          :image="product.image"
          :price="product.price"
          v-on:toggle-event="clikBtn"
        />
      </article>
    </div>
  </main>
</template>

<script>
import axios from 'axios'
import Card from './Card'

export default {
  name: 'Product',
  components: {
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
      axios.get('http://localhost:4000/api/v1/products').then((res) => {
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
</style>

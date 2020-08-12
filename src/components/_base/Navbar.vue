<template>
  <nav class="col-md-1 col-sm-1 p-md-3 p-sm-1">
    <img class="icon" src="../../assets/fork.png" @click="linkHome"/>
    <img class="icon" src="../../assets/clipboard.png" @click="linkHistory" />
    <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#myModal">
      <img class="icon" src="../../assets/add.png" />
    </button>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
  methods: {
    linkHistory () {
      this.$router.push({
        name: 'history'
        // params: { id: 5, name: 'risano', email: 'risa@gamil.com' },
        // query: { search: 'akbar' }
      })
    },
    linkHome () {
      this.$router.push({
        name: 'home'
      })
    }
  }
}
</script>

<style scoped>
.icon {
  width: 35px;
  height: 35px;
  margin-left: 5px;
}

/* Nav */

nav {
  background: #ffffff;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.25);
}

nav .icon {
  margin-top: 20px;
}

nav button.btn-primary {
  background-color: transparent;
  padding-left: 0;
  border: 0;
}
</style>

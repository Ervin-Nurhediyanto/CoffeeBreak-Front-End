<template>
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
              <img class="image-empty" src="../../assets/food-and-restaurant.png" />
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
</template>

<script>
export default {
  name: 'Sidebar'
}
</script>

<style scoped>

.image-empty {
  width: 250px;
  height: 270px;
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
</style>>

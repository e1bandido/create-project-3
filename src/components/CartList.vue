<template>
<div class="wrapper">
  <div class="products">
    <div class="product" v-for="(item, i) in this.$root.$data.cart" :key="i">
      <div class="info">
        <h1>{{item.name}}</h1>
        <p>{{item.country}}</p>
      </div>
      <div class="image">
        <img :src="'/images/products/'+item.image">
      </div>
      <div class="price">
        <h2>{{item.price}}</h2>
        <button @click="removeFromCart(item)" class="auto">Remove</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>

export default {
  name: 'CartList',
  props: {
    cart: Array
  },

  methods: {
    removeFromCart(removeItem) {

      const index = this.$root.$data.cart.indexOf(removeItem);
      // console.log(index)
      if (index > -1) {
        this.$root.$data.cart.splice(index, 1);
      }
      // console.log(this.$root.$data.cart)
    }
  }
}
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.products {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.product {
  margin: 10px;
  margin-top: 50px;
  width: 200px;
}

.product img {
  border: 2px solid #333;
  height: 250px;
  width: 200px;
  object-fit: cover;
}

.product .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #9dd3ff;
  color: #000;
  padding: 10px 30px;
  height: 80px;
}

.info h1 {
  font-size: 16px;
}

.info h2 {
  font-size: 14px;
}

.info p {
  margin: 0px;
  font-size: 10px;
}


.price {
  display: flex;
}

button {
  height: 50px;
  background: #000;
  color: white;
  border: none;
}

.auto {
  margin-left: auto;
}
</style>
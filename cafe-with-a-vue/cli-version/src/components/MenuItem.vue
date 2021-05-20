<template>
  <section class="menu">
    <h2>Menu</h2>
      <div v-for="item in simpleMenu" :key="item.name" class="menu-item">
        <img
          class="menu-item__image"
          :src="item.image.source"
          :alt="item.image.alt"
        />
        <div>
          <h3>{{ item.name }}</h3>
          <p v-if="item.inStock">En stock</p>
          <p v-else>En rupture de stock</p>
          <div>
            <label for="add-item-quantity"
              >Quantité : {{ item.quantity }}</label
            >
            <input
              v-model.number="item.quantity"
              id="add-item-quantity"
              type="number"
            />
            <button @click="addToShoppingCart(item.quantity)">
              Ajouter au panier d'achat
            </button>
          </div>
        </div>
      </div>
  </section>
</template>

<script>
export default {
  name: 'MenuItem',
  props: [ "addToShoppingCart","name", "image", "inStock", "quantity" ]
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

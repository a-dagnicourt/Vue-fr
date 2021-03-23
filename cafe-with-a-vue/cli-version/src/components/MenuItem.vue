<script>
export default {
  name: "MenuItem",
  props: ["addToShoppingCart", "image", "inStock", "name", "price", "quantity"],
  beforeMount() {
    const evenDay = () => new Date().getDay() % 2 === 0;
    evenDay() && (this.price = this.price * 0.9);
  },
};
</script>

<template>
  <div class="menu-item">
    <img class="menu-item__image" :src="image.source" :alt="image.alt" />
    <div>
      <h3>{{ name }}</h3>
      <p>Prix : {{ price.toFixed(2) }}</p>
      <p v-if="inStock">En stock</p>
      <p v-else>En rupture de stock</p>
      <div>
        <label for="add-item-quantity">Quantité : {{ quantity }}</label>
        <input v-model.number="quantity" id="add-item-quantity" type="number" />
        <button @click="addToShoppingCart(quantity)">
          Ajouter au panier
        </button>
      </div>
    </div>
  </div>
</template>

<style></style>

<script>
import { computed, ref, reactive, toRef, toRefs } from 'vue';
export default {
  setup() {
    const message = ref('Hello')
    const quantity = ref(1)
    const item = reactive({
      name: 'Product 1',
      price: 10
    })

    const increment = () => {
      quantity.value++
    }

    const decrement = () => {
      quantity.value--
    }

    const swapProduct = () => {
      item.name = 'Product A',
      item.price = 30
    }

   const total = computed(() => item.price * quantity.value)

    // const nameRef = toRef(item, 'name');

    // console.log("nameRef: ",nameRef.value);

    // item.name = 'New Product';

    // console.log("nameRef: ",nameRef.value); 

    // const itemRefs = toRefs(item);

    // console.log("name: ",itemRefs.name.value);
    // console.log("price: ",itemRefs.price.value);

    // item.name = 'Hot Product';
    // item.price = 50;

    // console.log("name: ",itemRefs.name.value);
    // console.log("price: ",itemRefs.price.value);

    const { name, price } = toRefs(item);

    return { 
      message,
      quantity,
      increment,
      decrement,
      // item,
      name,
      price,
      total,
      swapProduct
    }
  },
};
</script>

<template>
  <!-- <h1>{{ item.name }} : {{ item.price }}</h1> -->
  <h1>{{ name }} : {{ price }}</h1>
  <button @click="swapProduct">Swap Product</button>
  <button @click="price++">Increment Price</button>

  <h1>{{ message }}</h1>
  <input v-model="message" />
  <h2>{{ quantity }}</h2>
  <button @click="increment">Increment</button>
  <button @click="decrement">Decrement</button>

  <h3>Total: {{ total }}</h3>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>

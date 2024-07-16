<script setup>
import CartItem from './components/CartItem.vue';
import useCart from './useCart';

const { items, addItem, removeItem} = useCart()

addItem({
        id: 1,
        name: 'Product X',
        price: 20,
        quantity: 1 
      })

</script>
<script>
// import { ref } from 'vue';
// import { computed, ref, reactive, toRef, toRefs, watch, watchEffect } from 'vue';
// export default {
//   setup() {
//     const message = ref('Hello')
//     // const quantity = ref(1)
//     const item = reactive({
//       name: 'Product 1',
//       price: 10,
//       quantity: 1
//     })

//     const increment = () => {
//       item.quantity++
//     }

//     const decrement = () => {
//       item.quantity--
//     }

//     const swapProduct = () => {
//       item.name = 'Product A',
//       item.price = 30
//     }

//    const total = computed(() => item.price * item.quantity)

//     // const nameRef = toRef(item, 'name');

//     // console.log("nameRef: ",nameRef.value);

//     // item.name = 'New Product';

//     // console.log("nameRef: ",nameRef.value); 

//     // const itemRefs = toRefs(item);

//     // console.log("name: ",itemRefs.name.value);
//     // console.log("price: ",itemRefs.price.value);

//     // item.name = 'Hot Product';
//     // item.price = 50;

//     // console.log("name: ",itemRefs.name.value);
//     // console.log("price: ",itemRefs.price.value);

//     const { name, price, quantity } = toRefs(item);

//     watch(total, (newValue, oldValue) => {
//       console.log("newValue: ",newValue);
//       console.log("oldValue: ",oldValue);
//     }, { immediate: true })

//     // watching reactive object
//     watch(() => item.quantity, () => {
//       if (item.quantity === 5) {
//         alert("You cannot add more items");
//       }
//     }, {immediate: true})

//     watchEffect(() => {
//       console.log("Price changed: ",item.price);
//     })

//     return { 
//       message,
//       quantity,
//       increment,
//       decrement,
//       // item,
//       name,
//       price,
//       total,
//       swapProduct
//     }
//   },
// };

// import CartItem from './components/CartItem.vue';
// import useCart from './useCart';

// export default {
//   components: { CartItem },

//   setup () {

//     const { items, addItem, removeItem} = useCart();

    // const items = ref([
    //   {
    //     id: 1,
    //     name: 'Product X',
    //     price: 20,
    //     quantity: 1 
    //   }
    // ])

    // addItem({
    //     id: 1,
    //     name: 'Product X',
    //     price: 20,
    //     quantity: 1 
    //   })

    // const handleRemove = (data) => items.value.splice(0, 1)

//     return { items, removeItem }
//   }
// }

</script>
  
<template>
  <!-- <h1>{{ item.name }} : {{ item.price }}</h1> -->
  <!-- <h1>{{ name }} : {{ price }}</h1>
  <button @click="swapProduct">Swap Product</button>
  <button @click="price++">Increment Price</button>

  <h1>{{ message }}</h1>
  <input v-model="message" />
  <h2>{{ quantity }}</h2>
  <button @click="increment">Increment</button>
  <button @click="decrement">Decrement</button>

  <h3>Total: {{ total }}</h3> -->
  <CartItem v-for="item in items" :cart-item="item" :key="item.id" @remove="removeItem" />
</template>

<style scoped>

</style>

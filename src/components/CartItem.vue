<script setup>
import {
  computed,
  reactive,
  toRefs,
  onUpdated,
  onUnmounted,
  onMounted,
} from "vue";

const props = defineProps({
  cartItem: {
    type: Object,
    required: true,
  },
});

const emit = defineEmits(["remove"]);

// console.log("props: ",props.cartItem);
const item = reactive(props.cartItem);

const increment = () => {
  item.quantity++;
};

const decrement = () => {
  item.quantity--;
};

const total = computed(() => item.price * item.quantity);
const { name, price, quantity } = toRefs(item);

//  const remove = () => alert("Remove item");
// const remove = () => context.emit('remove', item);

const remove = () => emit("remove", item); // ccontext is removed from setup() function

onMounted(() => {
  console.log("Component mounted");
});

onUpdated(() => {
  console.log("Component updated");
});

onUnmounted(() => {
  console.log("Component unmounted");
});
</script>
<script>
// import { computed, reactive, toRefs, onUpdated, onUnmounted, onMounted } from 'vue';

// export default {

//     props: {
//       cartItem: {
//         type: Object,
//         required: true
//       },
//     },
//     emits: ['remove'],
//   setup(props, { emit }) {
// console.log("props: ",props.cartItem);
// const item = reactive(props.cartItem)

// const increment = () => {
//   item.quantity++
// }

//   const decrement = () => {
//     item.quantity--
//   }

//  const total = computed(() => item.price * item.quantity)
//  const { name, price, quantity } = toRefs(item);

//  const remove = () => alert("Remove item");
// const remove = () => context.emit('remove', item);

//   const remove = () => emit('remove', item); // ccontext is removed from setup() function

//   onMounted(() => {
//     console.log("Component mounted");
//   })

//   onUpdated(() => {
//     console.log("Component updated");
//   })

//   onUnmounted(() => {
//     console.log("Component unmounted");
//   })

//     return {
//         remove,
//       quantity,
//       increment,
//       decrement,
//       // item,
//       name,
//       price,
//       total
//     }
//   },
// };
</script>

<template>
  <h1>{{ name }} : {{ price }} {{ quantity }}</h1>

  <button @click="increment">Increment</button>
  <button @click="decrement">Decrement</button>
  <br />
  <button @click="remove">Remove</button>

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

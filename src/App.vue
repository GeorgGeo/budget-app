<template>
  <div>
    <div class="price-block">
      <p>Original Price: {{ originalPrice }}</p>
      <input type="number" v-model="discount">
      <p>Discount: {{ discount }}</p>
      <p>Finally Price: {{ finallyPrice }}</p>
    </div>

    <MethodsVue />

    <!-- Обчисліть загальну вартість телефонів студентів вашого класу, використавши метод computed. При бажанні можете вивести дані на екран. -->
     <div class="price-student">
      <p>Total Price: {{ totalPrice }}</p>
     </div>
  </div>
</template>

<script>
import { defineComponent, ref, computed } from 'vue';
import MethodsVue from './components/MethodsVue.vue';

// import HelloWorld from './components/HelloWorld.vue'

export default defineComponent({
  name: 'App',
  components: {
    // HelloWorld
    MethodsVue,
  },
  setup() {

    const originalPrice = ref(100);
    const discount = ref(null);

    console.log(originalPrice);

    const finallyPrice = computed(() => {
      return originalPrice.value - discount.value;
    });
    // Homework
    const studentList = ref([
      {
        name: 'Yuriy',
        age: 29,
        phone: 'Apple',
        price: 2900,
      },
      {
        name: 'Vika',
        age: 39,
        phone: 'Samsung',
        price: 1900,
      },
      {
        name: 'Vova',
        age: 25,
        phone: 'Apple',
        price: 2000,
      },
      {
        name: 'Vita',
        age: 29,
        phone: 'Apple',
        price: 3000,
      },
    ]);

    const totalPrice = computed(() => {
      return studentList.value.reduce((acc, item) => acc += item.price, 0)
    });

    return {
      originalPrice,
      discount,
      finallyPrice,
      // Homework
      studentList,
      totalPrice
    }
  }
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

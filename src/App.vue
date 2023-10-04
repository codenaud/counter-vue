<!-- Script -->
<script setup>
import { ref, computed } from 'vue';

//metodos reactivos - (línea 160)
const counter = ref(0);
const increment = () => {
  console.log('Aumentar contador');
  counter.value++;
  console.log(counter.value);
};
const decrement = () => {
  counter.value--;
};
const resetButton = () => {
  counter.value = 0;
};

const classCounter = computed(() => {
  if (counter.value === 0) {
    return 'zero';
  }
  if (counter.value > 0) {
    return 'positive';
  }
  if (counter.value < 0) {
    return 'negative';
  }
});

const arrayFavoritos = ref([]);
const add = () => {
  arrayFavoritos.value.push(counter.value);
};
const bloquearBtnAdd = computed(() => {
  const numSearch = arrayFavoritos.value.find((num) => num === counter.value);
  console.log(numSearch);
  // if (numSearch === 0) return true;
  // return numSearch ? true : false;

  return numSearch || numSearch === 0;
});
</script>

<!-- Template -->
<template>
  <!-- Métodos reactivos importar ref y aignarle el método computed para agregar el valor de los colores-->
  <div class="container">
    <h2>Métodos reactivos:</h2>
    <h3>Ejemplo contador</h3>

    <h2 :class="classCounter">{{ counter }}</h2>
    <div class="btn-group margin-bottom">
      <button @click="increment()" class="btn btn-success">Aumentar</button>
      <button @click="decrement()" class="btn btn-danger">Disminuir</button>
      <button @click="resetButton()" class="btn btn-secondary">Resetear</button>
      <button @click="add()" :disabled="bloquearBtnAdd" class="btn btn-primary">Add</button>
    </div>
    <br />
    <p>{{ arrayFavoritos }}</p>
    <br />
    <ul class="list-group">
      <li class="list-group-item" v-for="(num, index) in arrayFavoritos" :key="index">
        {{ num }}
      </li>
    </ul>
  </div>
</template>

<!-- Style -->
<style>
.positive {
  color: green;
}
.negative {
  color: red;
}
.zero {
  color: blue;
}
.margin-bottom {
  margin-bottom: 10px;
}
#app {
  display: flex;
}
.container {
  text-align: center;
}
</style>

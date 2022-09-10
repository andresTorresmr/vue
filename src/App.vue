<script setup>
import { ref, computed } from "vue";
const name = "Vue dinámico";
const texto = ref("");
const counter = ref(0);
const nombre = ref([]);
const increment = () => {
  counter.value++;
};
const decrement = () => {
  counter.value--;
};
const reset = () => {
  counter.value = 0;
};
const addName = computed(() => {
  nombre.value.push(texto.value);
  texto.value = "";
});
const classColor = computed(() => {
  if (counter.value < 0) {
    return "text-danger";
  }
  if (counter.value > 0) {
    return "text-success";
  }
  if (counter.value == 0) {
    return "text-primary";
  }
});
</script>

<template>
  <h1>{{ name.toUpperCase() }}</h1>

  <h2>Contador</h2>
  <h3 :class="classColor">{{ counter }}</h3>
  <div class="btn-group">
    <button @click="increment" class="btn btn-primary">Aumentar</button>
    <button @click="decrement" class="btn btn-danger">Disminuir</button>
    <button @click="reset" class="btn btn-warning">Resetear</button>
  </div>

  <div class="mt-5">
    <h3>Texto: {{ texto }}</h3>
    <br />
    <div class="input-group flex-nowrap">
      <input
        v-model="texto"
        type="text"
        class="form-control"
        placeholder="Ingresa un texto"
        @keyup.enter="addName"
      />
    </div>
    <br />
    <br />
    <h2>Unidades computadas</h2>

    <table class="table table-dark table-striped mt-5">
      <thead>
        <tr>
          <th>Nombre</th>
        </tr>
      </thead>
      <tbody>
        <template v-for="names in nombre">
          <tr>
            <td>{{ names }}</td>
          </tr>
        </template>
      </tbody>
    </table>
  </div>
</template>

<style></style>

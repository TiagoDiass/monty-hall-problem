<template>
  <div id="app">
    <h1>Problema de Monty Hall</h1>
    <div class="form">
      <div v-if="!started">
        <label for="doorsAmount">Quantas Portas?</label>
        <input type="text" id="doorsAmount" size="3" v-model.number="doorsAmount" />
      </div>
      <div v-if="!started">
        <label for="selectedDoor">Qual porta é premiada?</label>
        <input type="text" id="selectedDoor" size="3" v-model.number="selectedDoor" />
      </div>
      <button v-if="!started" @click="started = true">Iniciar</button>
      <button v-if="started" @click="started = false">Reiniciar</button>
    </div>
    <div class="doors" v-if="started">
      <div v-for="i in doorsAmount" :key="i">
        <Door :number="i" :hasGift="i === selectedDoor" />
      </div>
    </div>
  </div>
</template>

<script>
import Door from "./components/Door";

export default {
  name: "App",
  components: { Door },
  data: function() {
    return {
      started: false,
      doorsAmount: 3,
      selectedDoor: null
    };
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  font-family: "Monserrat", sans-serif;
}

body {
  color: #fff;
  background: linear-gradient(to right, rgb(21, 153, 87), rgb(21, 87, 153));
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}

#app h1 {
  border: 1px solid #000;
  background-color: #0004;
  padding: 20px;
  margin-bottom: 60px;
}

.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 40px;
}

.form label,
.form input,
.form button {
  margin-bottom: 10px;
  font-size: 1.7rem;
  padding: 6px;
  border-radius: 4px;
  border: none;
  outline: none;
}

.form input {
  margin-left: 8px;
}

.form button {
  background-color: white;
  transition: background 0.1s;
}

.form button:hover {
  background-color: #eee;
  cursor: pointer;
}

.doors {
  align-self: stretch;
  display: flex;
  justify-content: space-around;

  flex-wrap: wrap;
  margin-top: 50px;
}
</style>
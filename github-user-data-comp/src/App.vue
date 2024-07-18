<script setup>
import Composition from './components/Composition.vue'
</script>

<template>
  <Composition />
</template>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background-color: #1c1a1d;
  color: #e5e5e5;
}

#app {
  font-family: Arial, Helvetica, sans-serif;
  min-height: 100vh;
  max-width: 40rem;
  margin: 0 auto;
  text-align: center;
}

img {
  border: 1px solid #e5e5e5;
  border-radius: 999px;
  display: block;
  margin: 1rem auto;
  width: 8rem;
  height: 8rem;
}

h1,
h2 {
  color: #e143f65d;
  margin: 1rem auto 0.25rem;
}

h3 {
  margin: 1rem auto 0.25rem;
}

span {
  display: block;
  margin: 1rem auto;
}

input,
button {
  max-width: 20rem;
  padding: 0.5rem;
}

input {
  background-color: #1c1a1d70;
  border: 1px solid #d243f61f;
  border-radius: 0.25rem;
  color: #e5e5e5;
  margin: 1rem 1rem 1rem 0;
}

button {
  background-color: #e5e5e5;
  border: unset;
  border-radius: 0.25rem;
  color: #1c1a1d;
  font-size: 1rem;
  font-weight: 700;
  text-transform: uppercase;
}

button:hover {
  cursor: pointer;
  filter: brightness(0.95);
}

a {
  color: #f64348;
}
</style>

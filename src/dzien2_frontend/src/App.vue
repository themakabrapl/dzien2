<script setup>
import { ref } from 'vue';
import { dzien2_backend } from 'declarations/dzien2_backend/index';
import Blog from './commponents/Blog.vue';
let greeting = ref('');

async function handleSubmit(e) {
  e.preventDefault();
  const target = e.target;
  const name = target.querySelector('#name').value;
  const number = target.querySelector('#number').value;
  await dzien2_backend.greet(name, Number(number)).then((response) => {
    greeting.value = response;
  });
}
</script>

<template>
  <main>
    <img src="/logo2.svg" alt="DFINITY logo" />
    <br />
    <br />
    <form action="#" @submit="handleSubmit">
      <label for="name">Enter your name: &nbsp;</label>
      <input id="name" alt="Name" type="text" />
      <input id="number" alt="Number" type="number" />
      <button type="submit">Click Me!</button>
    </form>
    <section id="greeting">{{ greeting }}</section>
  </main>
</template>

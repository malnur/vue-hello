<script setup>
import { reactive, ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'

const message = ref('Hello Vue.js!')

const headingClass = ref('green')

const type = ref('B')
const ok = ref(true)

const books = reactive(['book-1', 'book-2', 'book-3', 'book-4'])

const users = reactive([
  {
    name: 'User-1',
    age: 23,
    books: 3
  },
  {
    name: 'User-2',
    age: 15,
    books: 6
  },
  {
    name: 'User-3',
    age: 40,
    books: 5
  }
])

const count = ref(0)
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />
    <div class="wrapper">
      <h1>{{ message }}</h1>
    </div>
  </header>

  <main>
    <section>
      <h2 :class="headingClass">Binding</h2>
      <p>{{ message.split('').reverse().join('') }}</p>
    </section>

    <section>
      <h2>Conditional</h2>
      <div v-if="type === 'A'">A</div>
      <div v-else-if="type === 'B'">B</div>
      <div v-else-if="type === 'C'">C</div>
      <div v-else>Not A/B/C</div>

      <div v-show="ok">On show message</div>
    </section>

    <section>
      <h2>List Items</h2>
      <ul>
        <li v-for="(book, index) in books" :key="index" class="green">
          {{ book }}
        </li>
      </ul>
      <hr />
      <ol>
        <li v-for="(user, index) in users" :key="index" class="green">
          {{ user.name }} has {{ user.books }} books
        </li>
      </ol>
    </section>

    <section>
      <h2>Event Handler</h2>
      <div>
        <button @click="count++">Counter</button>
        <button @click="count++">Counter</button>
        <span class="green">{{ count }}</span>
      </div>
    </section>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

section {
  margin-bottom: 1.5rem;
}

section h2 {
  text-align: center;
  margin-bottom: 0.5rem;
}

section hr {
  margin: 0.5rem 0;
  border: 1px solid var(--color-text);
}

section button {
  padding: 0.5rem 1rem;
  color: white;
  border: 1px solid var(--color-text);
  border-radius: 4px;
  background-color: transparent;
  margin-right: 1rem;
}

section span {
  font-size: 1.5rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>

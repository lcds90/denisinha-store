
<template>
  <div class="layout-store">
    <Header />
    <aside class="aside">
      <!--  <p v-if="$fetchState.pending">
        Fetching mountains...
      </p>
      <p v-else-if="$fetchState.error">
        An error occurred :(
      </p>
      <div v-else>
        <h1>Nuxt Mountains</h1>
        <ul>
          <li v-for="mountain of mountains" :key="mountain.title">
            {{ mountain.title }}
          </li>
        </ul>
        <button @click="$fetch">
          Refresh
        </button>
      </div> -->
    </aside>
    <main class="main">
      <ul>
        <li
          v-for="todo in todos"
          :key="todo.text"
        >
          <input
            :checked="todo.done"
            type="checkbox"
            @change="toggle(todo)"
          >
          <span :class="{ done: todo.done }">{{ todo.text }}</span>
        </li>
        <li>
          <input
            placeholder="What needs to be done?"
            @keyup.enter="addTodo"
          >
        </li>
      </ul>
    </main>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { mapMutations } from 'vuex'

export default Vue.extend({
  data () {
    return {
      show: true,
      title: 'Loja da denisinha!'
    }
  },
  async fetch () {
    const data = await fetch(
      'https://api.nuxtjs.dev/mountains'
    ).then(res => res.json())
    this.$store.commit('todos/setList', data)
  },
  head () {
    return {
      title: this.title,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: 'description',
          name: 'description',
          content: 'My custom description'
        }
      ]
    }
  },
  computed: {
    todos () {
      return this.$store.state.todos.list
    }
  },
  methods: {
    addTodo (e) {
      this.$store.commit('todos/add', e.target.value)
      e.target.value = ''
    },
    ...mapMutations({
      toggle: 'todos/toggle'
    })
  }
})
</script>

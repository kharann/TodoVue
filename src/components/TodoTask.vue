<template>
  <li>
    <label :style="[todo.done ? {'text-decoration': 'line-through'} : {}]">
      <input
        v:model="done"
        v-on:click="check(todo)"
        :checked="todo.done"
        type="checkbox"
        class="nes-checkbox"
      />
      <span>{{todo.text}}</span>
    </label>
    <button v-on:click="deleteTodo(todo)" class="nes-btn is-error">X</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      text: String,
      done: Boolean,
      id: Date
    }
  },
  methods: {
    check(todo) {
      todo.done = !todo.done;
    },
    deleteTodo(todo) {
      this.$emit("lol", todo.id);
    }
  }
};
</script>

<style scoped>
li {
  list-style: none;
  display: flex;
  justify-content: space-between;
  margin: 20px 0 0 20px;
}

label {
  display: flex;
  align-items: center;
  font-size: 20px;
}

button {
  margin-right: 10px;
}
</style>
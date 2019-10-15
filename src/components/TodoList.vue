<template>
  <div id="todo">
    <h1>TODOS</h1>
    <div class="nes-field" id="addTodoContainer">
      <input v-model="taskName" type="text" class="nes-input" placeholder="Add todo..." />
      <button v-on:click="handleAddTodo" class="nes-btn">add task</button>
    </div>
    <todo-task v-for="todo in todos" :key="todo.id" :todo="todo" @lol="deleteTodo"></todo-task>
  </div>
</template>

<script>
import TodoTask from "./TodoTask.vue";

export default {
  data() {
    return {
      todos: [
        { text: "todo 1", done: true, id: Date.now() },
        { text: "todo 2", done: false, id: Date.now() + 1 }
      ]
    };
  },
  components: {
    TodoTask
  },

  methods: {
    handleAddTodo() {
      this.taskName &&
        this.todos.push({ text: this.taskName, done: false, id: Date.now() });
      this.taskName = "";
    },

    deleteTodo(id) {
      this.todos = this.todos.filter(x => x.id != id);
    }
  }
};
</script>

<style>
#addTodoContainer {
  display: flex;
  flex-direction: row;
}
#addTodoContainer > button {
  margin-left: 10px;
}
</style>

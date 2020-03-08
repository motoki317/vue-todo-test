<template>
  <div>
    <h2>ToDo-List</h2>
    <h3>やること</h3>
    <div v-for="todo in activeTodos" :key="todo.name">
      <div class="todo" :class="{ finished: todo.finished }">
        {{ todo.name }}
      </div>
      <button
        v-bind:disabled="todo.finished"
        @click="todo.finished = !todo.finished"
      >
        完了
      </button>
      <button
        v-bind:disabled="!todo.finished"
        @click="todo.finished = !todo.finished"
      >
        未完了
      </button>
    </div>
    <h3>終わったこと</h3>
    <div v-for="todo in inactiveTodos" :key="todo.name">
      <div class="todo" :class="{ finished: todo.finished }">
        {{ todo.name }}
      </div>
      <button
        v-bind:disabled="todo.finished"
        @click="todo.finished = !todo.finished"
      >
        完了
      </button>
      <button
        v-bind:disabled="!todo.finished"
        @click="todo.finished = !todo.finished"
      >
        未完了
      </button>
    </div>
    <p>
      <label for>
        ToDoを追加
        <input type="text" v-model="newTodo" />
        <button @click="add">追加</button>
      </label>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  data() {
    return {
      newTodo: "",
      todos: [
        {
          name: "This is a test to-do",
          finished: false
        }
      ]
    };
  },
  methods: {
    add: function() {
      this.todos.push({
        name: this.newTodo,
        finished: false
      });
      this.newTodo = "";
    }
  },
  computed: {
    activeTodos() {
      return this.todos.filter(function(todo) {
        return !todo.finished;
      });
    },
    inactiveTodos() {
      return this.todos.filter(function(todo) {
        return todo.finished;
      });
    }
  }
};
</script>

<style>
.todo {
  margin: 0 auto;
}

.finished {
  color: #888888;
}
</style>

<template>
  <div class="forum">
    <div>
      <p>Vue Course</p>
    </div>
    <div>
      <NewTodo @on-addtodo="addTodo($event)" />
    </div>
    <div>
      <ul>
        <Todo
          v-for="(todo, index) in todos"
          :key="index"
          :todoString="todo.todoString"
          :completed="todo.completed"
          @on-delete="deleteTodo(todo)"
          @on-toggle="toggleTodo(todo)"
          @on-edit="editTodo(todo, $event)"
        />
      </ul>
    </div>
  </div>
</template>

<script>
import NewTodo from "./NewTodo";
import Todo from "./Todo";
export default {
  components: {
    Todo,
    NewTodo,
  },
  data() {
    return {
      todos: [
        { todoString: "Hello World !!!", completed: false },
        { todoString: "Hello Nigga !!!", completed: true },
        { todoString: "https://colorhunt.co/palette/195948", completed: false },
      ],
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push({ todoString: newTodo, completed: false });
    },
    toggleTodo(todo) {
      todo.completed = !todo.completed;
    },
    editTodo(todo, newTodoString) {
      todo.todoString = newTodoString;
    },
    deleteTodo(deleteTodo) {
      this.todos = this.todos.filter((todo) => todo !== deleteTodo);
    },
  },
};
</script>

<style scoped>
.forum {
  width: 90%;
  margin: auto;
}

div > p {
  color: #cdb30c;
  text-align: center;
  font-size: 28px;
}

ul {
  margin: 0;
  padding: 0;
}

@media only screen and (min-width: 1000px) {
  .forum {
    width: 60%;
  }
}
</style>
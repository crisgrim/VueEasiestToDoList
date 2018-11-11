<template>
  <div>
    <BaseInputText
    v-model="newTodoText"
    placeholder="New todo"
    @keydown.enter="addTodo"
    />
    <ul v-if="todos.length">
      <TodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @remove="removeTodo"
      @markDone="markDone"
      />
    </ul>
    <p v-else>Write some TODO item here</p>
  </div>
</template>

<script>
import BaseInputText from "./BaseInputText.vue";
import TodoItem from "./TodoItem.vue";

let nextTodoId = 1;

export default {
  components: {
    BaseInputText,
    TodoItem
  },
  data() {
    return {
      newTodoText: "",
      todos: [
        {
          id: nextTodoId++,
          text: "Learn Vue",
          done: false
        },
        {
          id: nextTodoId++,
          text: "Learn React",
          done: false
        },
        {
          id: nextTodoId++,
          text: "Learn Angular",
          done: false
        },
        {
          id: nextTodoId++,
          text: "Learn Polymer",
          done: false
        }
      ]
    };
  },
  methods: {
    addTodo() {
      const trimmedText = this.newTodoText.trim();
      if (trimmedText) {
        this.todos.push({
          id: nextTodoId++,
          text: trimmedText,
          done: false
        });
        this.newTodoText = "";
      }
    },
    removeTodo(idToRemove) {
      this.todos = this.todos.filter(todo => {
        return todo.id !== idToRemove;
      });
    },
    markDone(id) {
      this.todos.find(obj => {
        if (obj.id === id) {
          obj.done = true;
        }
        return obj.id === id;
      });
    }
  }
};
</script>

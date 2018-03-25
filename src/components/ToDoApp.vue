<template>
  <div class="todo-app">
    <todo-input 
      v-model="newTodoText"
			placeholder="New todo"
			@keydown.enter="addTodo"
    />
    <todo-list :todos="todos" />
  </div>
</template>

<style scoped>
    .todo-app {
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
        margin-top: 50px;
        height: 100vh;
    }
</style>


<script>
import TodoInput from './ToDoInput.vue';
import TodoList from './ToDoList.vue';
import { EventBus } from './../event-bus.js';

let nextTodoId = 0;

export default {
  components: { TodoInput, TodoList },
  data () {
    return {
      newTodoText: '', 
      todos: []
    }
  },
  methods: {
    addTodo () {
			const trimmedText = this.newTodoText.trim()
			if (trimmedText) {
				this.todos.push({
					id: nextTodoId++,
					text: trimmedText
				})
				this.newTodoText = ''
			}
		},
		removeItemFromTodo (itemId) {
			this.todos = this.todos.filter(todo => {
				return todo.id !== itemId
			})
    }
  },
  mounted() {
    EventBus.$on('removeItem', this.removeItemFromTodo);
  }
}
</script>

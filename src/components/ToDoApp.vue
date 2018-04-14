<template>
  <div class="todo-app">
    <input 
      v-model="newTodoText"
			placeholder="New todo"
			@keydown.enter="addTodo"
    />
    <ul v-if="todos.length">
        <todo-list-item
            v-for="todo in todos"
            :key="todo.id"
            :todo="todo"
        />
    </ul>
    <p v-else>
        Nothing left in the list. Add a new todo in the input above.
    </p>
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

    .input {
        padding: 8px 10px;
        border: 2px solid darkblue;
        min-width: 300px;
    }

    ul {
      list-style-type: none;
      width: 300px;
    }

    li {
        margin-bottom: 5px;
    }
</style>


<script>
import TodoListItem from './TodoListItem.vue';
import { EventBus } from './../event-bus.js';

let nextTodoId = 0;

export default {
  components: { TodoListItem },
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

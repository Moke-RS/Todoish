<template>
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
</template>

<style scoped>
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

let nextTodoId = 0;

export default {
    components: {
		TodoListItem
    },
    props: {
        todos: {
            type: Array,
            required: true
        }
    }
}
</script>

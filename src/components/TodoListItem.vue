<template>
  <li :class="{ 'done' : done }">
    <span class="item-text">{{ todo.text }}</span>
    <span class="item-options">
      <button @click="toggleDoneStatus">
        {{ this.done ? "U" : "D" }}
      </button>
      <button @click="removeItem">
        X
      </button>
    </span>
  </li>
</template>

<style scoped>
li {
  display: flex;
  justify-content: space-between;
}

li.done span.item-text {
  color: gray;
  text-decoration: line-through;
}

.item-options {
  margin-left: 10px;
}

.item-options button {
  margin: 0px 5px;
}
</style>


<script>
import { EventBus } from './../event-bus.js';

export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      done: false
    }
  },
  methods: {
    removeItem() {
      EventBus.$emit('removeItem', this.todo.id)
    },
    toggleDoneStatus() {
      this.done = !this.done;
    }
  }
}
</script>


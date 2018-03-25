<template>
  <div class="todo-input">
      <base-input :value="inputValue" :placeholder="placeholder" :listeners="listeners" />
  </div>
</template>

<style scoped>
input {
    min-width: 300px;
}
</style>


<script>
import BaseInput from './BaseInputText.vue';

export default {
    components: { BaseInput },
    props: {
        value: {
            type: String,
            default: '',
        },
        placeholder: {
            type: String,
            default: ''
        }
    },
    data () {
        return {
            newTodoText: ''
        }
    },
    computed: {
        listeners () {
            return {
                // Pass all component listeners directly to BaseInput
                ...this.$listeners,
                // Override input listener to work with v-model
                input: event => this.$emit('input', event.target.value)
            }
        },
        inputValue () {
            return this.value;
        }
    }
}
</script>

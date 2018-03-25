<template>
  <input type="text" class="input" :placeholder="placeholder" :value="value" v-on="listeners" />
</template>

<script>
export default {
    props: {
        listeners: {
            type: Object
        },
        value: {
            type: String,
            default: '',
        },
        placeholder: {
            type: String,
            default: '',
        }
    }
}
</script>

<style scoped>
    .input {
        padding: 8px 10px;
        border: 2px solid darkblue;
    }
</style>

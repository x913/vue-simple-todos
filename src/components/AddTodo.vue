<template>
  <form @submit.prevent="onSubmit">
      <input type="text" v-model="text" placeholder="Add new todo">
      <button type="submit">Create</button>
  </form>
</template>

<script>
export default {
    data() {
        return {
            text: ''
        }
    },
    methods: {
        onSubmit() {
            this.$emit('add-todo', this.text);
            this.text = '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
        margin-bottom: 25px;
    }

    textarea:focus, input:focus{
        outline: none;
    }

    input {
        margin: 5px;
        width: 400px;
        border-style: none;
        border-bottom: 1px solid #000;
    }

    input:focus {
        border-style: none;
        border-bottom: 2px solid #000;
    }

</style>
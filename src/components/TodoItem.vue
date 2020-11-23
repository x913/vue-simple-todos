<template>
  <li>
      <span v-bind:class="{done: todo.completed}">
          <input type="checkbox" v-on:change="todo.completed = !todo.completed">
          <strong>{{todo.id}}</strong>
          {{todo.title}}
      </span>
      <button class="rm" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        }
    }
}
</script>


<style scoped>

    input {
        margin-right: 1rem;
    }

    li {
        border: 1px solid #ccc;
        display: flex;
        justify-content: space-between;
        padding: .5rem 2rem;
        margin-bottom: 1rem;

    }

    .rm {
        background: red;
        border-style: none;
        border-radius: 50%;
        color: #fff;
    }

    .done {
        text-decoration: line-through;
    }

</style>
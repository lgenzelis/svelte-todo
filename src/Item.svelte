<script>
  export let todo;
</script>

<style>
  .crossed {
    text-decoration: line-through;
  }
</style>

<li on:click class:crossed={todo.done}>{todo.text}</li>


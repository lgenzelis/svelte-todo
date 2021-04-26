<script>
  export let todo;
</script>

<style>
  li {
    list-style-type: none;
    font-weight: bold;
  }

  li::before {
    content: '✅';
    margin-right: 5px;
  }

  .crossed {
    text-decoration: line-through;
  }

  li.crossed {
    list-style-type: none;
    font-weight: normal;
    filter: grayscale(0.6);
  }

</style>

<li on:click class:crossed={todo.done}>{todo.text}</li>


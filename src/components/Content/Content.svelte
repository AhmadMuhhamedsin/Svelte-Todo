<script>
  let newItem = '';

  let todoList = [
    { text: 'first todo', status: false },
    { text: 'Hello', status: false },
    { text: 'World', status: false }
  ];

  function addToList() {
    todoList = [...todoList, { text: newItem, status: false }];
    newItem = '';
  }

  function removeFromList(index) {
    todoList.splice(index, 1);
    todoList = todoList;
  }
</script>
<div class="container">
  <input class=textinput bind:value={newItem} type="text" placeholder="Write a new todo item!">
  <button on:click={addToList}>Add</button>
  
  <br />
  
  {#each todoList as item, index}
    <div>
      <input bind:checked={item.status} type="checkbox">
      <span class:checked={item.status ? 'checked' : ''}>{item.text}</span>
      <span on:click={() => removeFromList(index)}>❌</span>
    </div>
  {/each}
</div>


<style>
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  .textinput {
    margin-bottom: 10px;
  }

  .checked {
    text-decoration: line-through;
  }
</style>
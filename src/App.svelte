<script>
  let items = [];

  function handleItemAdd() {
    const input = document.getElementById("item-input");
    items = [...items, { title: input.value, checked: false }];
    input.value = "";
  }
</script>

<div class="container">
  <h2>What would you like to achieve today?</h2>
  <div class="input-container">
    <input
      id="item-input"
      type="text"
      placeholder="Take the dog for a walk..."
    />
    <button on:click={handleItemAdd}> Add to list </button>
  </div>
  <div>
    <ul class="task-list">
      {#each items as { title, checked }, i}
        <li>
          <input type="checkbox" bind:checked={items[i].checked} />
          <p class:checked>
            {title}
          </p>
        </li>
      {/each}
    </ul>
  </div>
</div>

<style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .input-container {
    flex-direction: row;
  }
  .task-list {
    list-style: none;
    width: 100%;
  }
  .task-list li {
    display: flex;
    align-items: center;
    column-gap: 1rem;
  }
  .checked {
    text-decoration: line-through;
  }
</style>

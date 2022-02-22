<script>
  export let search = "";
  const clear = () => {
    search = "";
  };
</script>

<nav class="navbar">
  <div class="input-group input-group-lg mx-2 shadow" >
    <label class="input-group-text disabled" for="search" style="background-color: cornflowerblue;"><i class="bi bi-search text-light" /></label>
    <input type="search" id="search" placeholder="Live Search" bind:value={search} />
    <button class="btn btn-secondary" on:click={clear}>&#10006;</button>
  </div>
</nav>

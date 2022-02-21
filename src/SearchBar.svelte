<script>
  export let search = "";
  const clear = () => {
    search = "";
  };
</script>

<nav class="navbar navbar-dark bg-dark my-2">
  <div class="input-group mx-2">
    <span class="input-group-text"><i class="bi bi-search" /></span>
    <input type="search" placeholder="Live Search" bind:value={search} />
    <button class="btn btn-secondary" on:click={clear}>&#10006;</button>
  </div>
</nav>

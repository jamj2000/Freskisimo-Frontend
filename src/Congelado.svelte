<script>
  export let congelado = {};
</script>

<div class="card" style="width: 18rem;">
  <div class="card-body">
    <div class="input-group mb-3">
      <span class="input-group-text" id="name">Name</span>
      <input
        type="text"
        class="form-control"
        aria-label="Name"
        aria-describedby="name"
        bind:value={congelado.nombre}
      />
    </div>

    <div class="input-group mb-3">
      <span class="input-group-text" id="price">Price</span>
      <input
        type="number"
        class="form-control"
        aria-label="Price"
        aria-describedby="price"
        bind:value={congelado.precio}
      />
      <span class="input-group-text" id="euro">€</span>
    </div>

    <div class="input-group mb-3">
      <span class="input-group-text" id="amount">Amount</span>
      <input
        type="number"
        class="form-control"
        aria-label="Amount"
        aria-describedby="amount"
        bind:value={congelado.cantidad}
      />
    </div>

    <slot />
  </div>
</div>

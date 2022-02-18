<script>
    export let congelado = {};
</script>

<div>
    <input type="text" bind:value={congelado.nombre} />
    <input type="number" bind:value={congelado.precio} />
    <input type="number" bind:value={congelado.cantidad} />
    <slot/>
</div>
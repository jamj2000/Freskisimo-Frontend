<script>
    export let congelado = {};
</script>

<div>
    <input type="text" value={congelado.nombre} />
    <input type="number" value={congelado.precio} />
    <input type="number" value={congelado.cantidad} />
    <slot/>
</div>
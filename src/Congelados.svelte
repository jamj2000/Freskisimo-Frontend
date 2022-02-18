<script>
    import { getContext, onMount } from "svelte";
    import { jsonData } from "./store";
    import Congelado from "./Congelado.svelte";
    
    const URL = getContext("URL");
    
    onMount(() => {
        fetch(URL.congelados)
            .then((response) => response.json())
            .then((data) => ($jsonData = data));
    });
</script>

<h1>CONGELADOS</h1>

{#each $jsonData as congelado}
    <Congelado congelado = {congelado}/>
{/each}
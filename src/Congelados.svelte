<script>
    import { getContext, onMount } from "svelte";
    import { jsonData } from "./store";
    import Congelado from "./Congelado.svelte";
    import SearchBar from "./SearchBar.svelte"
    
    const URL = getContext("URL");
    let search = ""
    
    onMount(() => {
        fetch(URL.congelados)
            .then((response) => response.json())
            .then((data) => ($jsonData = data));
    });

    $: regexp = new RegExp (search, "i");
    $: data = search 
    ? $jsonData.filter((i) => regexp.test(i.nombre)) 
    : $jsonData

</script>

<h1>CONGELADOS</h1>

<SearchBar bind:search />

{#each data as congelado}
    <Congelado congelado = {congelado}/>
{/each}
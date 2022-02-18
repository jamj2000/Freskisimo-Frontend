<script>
    import { getContext, onMount } from "svelte";
    import { jsonData } from "./store";
    import Congelado from "./Congelado.svelte";
    import SearchBar from "./SearchBar.svelte"
    import Button from "./Button.svelte";
    
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

<Congelado>
    <Button type="insert" collection="congelados"/>
    </Congelado>

{#each data as congelado}
    <Congelado congelado = {congelado}>
    <Button type="update" collection="congelados"/>
    <Button type="delete" collection="congelados"/>
    </Congelado>
{/each}
<script>
  import { getContext, onMount } from "svelte";
  import { jsonData } from "./store";
  import Congelado from "./Congelado.svelte";
  import SearchBar from "./SearchBar.svelte";
  import Button from "./Button.svelte";

  const URL = getContext("URL");
  let search = "";
  let congelado = {};

  onMount(() => {
    fetch(URL.congelados)
      .then((response) => response.json())
      .then((data) => ($jsonData = data));
  });

  $: regexp = new RegExp(search, "i");
  $: data = search
    ? $jsonData.filter((item) => regexp.test(item.nombre))
    : $jsonData;
</script>

<h1>CONGELADOS</h1>

<SearchBar bind:search />

<Congelado bind:congelado>
  <Button type="insert" collection="congelados" document={congelado} />
</Congelado>

{#each data as congelado}
  <Congelado {congelado}>
    <Button type="update" collection="congelados" document={congelado} />
    <Button type="delete" collection="congelados" document={congelado} />
  </Congelado>
{/each}

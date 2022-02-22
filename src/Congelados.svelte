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

<div class="row">
  <div class="col">
    <Congelado bind:congelado class="my-2">
      <Button type="insert" collection="congelados" document={congelado} />
    </Congelado>
  </div>
  <div class="col-8">
    <div class="hero-image hero-image-congelados">
      <div class="hero-text">
        <h2 class="fw-bold">CONGELADOS</h2>
        <p class="fst-italic">Food preserved by a freezing process</p>
      </div>
    </div>
  </div>
</div>

<SearchBar bind:search />

<div class="row row-cols-1 row-cols-md-4 g-4">
  {#each data as congelado}
    <Congelado {congelado}>
      <Button type="update" collection="congelados" document={congelado} />
      <Button type="delete" collection="congelados" document={congelado} />
    </Congelado>
  {/each}
</div>

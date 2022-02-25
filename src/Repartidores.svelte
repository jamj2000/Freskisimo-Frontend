<script>
  import { getContext, onMount } from "svelte";
  import { jsonData } from "./store";
  import Repartidor from "./Repartidor.svelte";
  import SearchBar from "./SearchBar.svelte";
  import Button from "./Button.svelte";

  const URL = getContext("URL");
  let search = "";
  let repartidor = {};

  onMount(() => {
    fetch(URL.repartidores)
      .then((response) => response.json())
      .then((data) => ($jsonData = data));
  });

  $: regexp = new RegExp(search, "i");
  $: data = search
    ? $jsonData.filter((item) => regexp.test(item.dni))
    : $jsonData;
</script>

<div class="row my-4">
  <div class="col">
    <div class="row my-2" >
      <div class="col-12 d-flex justify-content-center">
        <Repartidor bind:repartidor>
          <Button type="insert" collection="repartidores" document={repartidor} />
        </Repartidor>
      </div>

      <div class="col-12 mt-4 d-flex justify-content-center">
        <SearchBar bind:search />
      </div>
    </div>
  </div>

  <div class="col-8">
    <div class="hero-image hero-image-repartidores h-100 shadow">
      <div class="hero-text">
        <h2 class="fw-bold">REPARTIDORES</h2>
        <p class="fst-italic">A person employed to make deliveries of merchandise to purchasers</p>
      </div>
    </div>
  </div>
</div>

<div class="row row-cols-1 row-cols-md-4 g-4">
  {#each data as repartidor}
    <div class="col d-flex justify-content-center">
      <Repartidor {repartidor}>
        <Button type="update" collection="repartidores" document={repartidor} />
        <Button type="delete" collection="repartidores" document={repartidor} />
      </Repartidor>
    </div>
  {/each}
</div>

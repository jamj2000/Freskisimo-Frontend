<script>
  import { getContext, onMount } from "svelte";
  import { jsonData } from "./store";
  import Vehiculo from "./Vehiculo.svelte";
  import SearchBar from "./SearchBar.svelte";
  import Button from "./Button.svelte";

  const URL = getContext("URL");
  let search = "";
  let vehiculo = {};

  onMount(() => {
    fetch(URL.vehiculos)
      .then((response) => response.json())
      .then((data) => ($jsonData = data));
  });

  $: regexp = new RegExp(search, "i");
  $: data = search
    ? $jsonData.filter((item) => regexp.test(item.matricula))
    : $jsonData;
</script>

<div class="row my-4">
  <div class="col">
    <div class="row my-2" >
      <div class="col-12 d-flex justify-content-center">
        <Vehiculo bind:vehiculo>
          <Button type="insert" collection="vehiculos" document={vehiculo} />
        </Vehiculo>
      </div>

      <div class="col-12 mt-4 d-flex justify-content-center">
        <SearchBar bind:search />
      </div>
    </div>
  </div>

  <div class="col-8">
    <div class="hero-image hero-image-vehiculos h-100 shadow">
      <div class="hero-text">
        <h2 class="fw-bold">VEHÍCULOS</h2>
        <p class="fst-italic">Machine with wheels and an engine, used for transporting, especially on land</p>
      </div>
    </div>
  </div>
</div>

<div class="row row-cols-1 row-cols-md-4 g-4">
  {#each data as vehiculo}
    <div class="col d-flex justify-content-center">
      <Vehiculo {vehiculo}>
        <Button type="update" collection="vehiculos" document={vehiculo} />
        <Button type="delete" collection="vehiculos" document={vehiculo} />
      </Vehiculo>
    </div>
  {/each}
</div>

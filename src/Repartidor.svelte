<script>
  import { getContext, onMount } from "svelte";
  export let repartidor = {};

  const URL = getContext("URL");
  let vehiculos = [];

  onMount(() => {
    fetch(URL.vehiculos)
      .then((response) => response.json())
      .then((data) => (vehiculos = data));
  });
</script>

<div class="card border-secondary shadow">
  <div class="card-body">
    <div class="input-group mb-3">
      <span class="input-group-text" id="dni">DNI</span>
      <input
        type="text"
        class="form-control"
        aria-label="DNI"
        aria-describedby="dni"
        bind:value={repartidor.dni}
      />
    </div>

    <div class="input-group mb-3">
      <span class="input-group-text" id="name">Name</span>
      <input
        type="text"
        class="form-control"
        aria-label="Name"
        aria-describedby="name"
        bind:value={repartidor.nombre}
      />
    </div>

    <div class="input-group mb-3">
      <span class="input-group-text" id="surname">Surname</span>
      <input
        type="text"
        class="form-control"
        aria-label="Surname"
        aria-describedby="surname"
        bind:value={repartidor.apellido}
      />
    </div>

    <div class="input-group mb-3">
      <span class="input-group-text" id="delivering">Delivering now</span>
      <div class="input-group-text">
        <input
          type="checkbox"
          class="form-check-input mt-0"
          aria-label="Delivering now"
          aria-describedby="delivering"
          bind:checked={repartidor.repartiendo}
        />
      </div>
    </div>

    <div class="input-group mb-3">
      <span class="input-group-text" id="vehiculo">Vehículo ID</span>
      <span class="input-group-text" id="textRegistration">
        {repartidor.vehiculoId !== undefined
          ? repartidor.vehiculoId.matricula
          : "Select below"}
      </span>
    </div>
    <select
      class="form-select mb-3"
      bind:value={repartidor.vehiculoId}
      aria-label="Vehículo"
    > 
      {#each vehiculos as vehiculo}
        <option value={vehiculo}>{vehiculo.matricula}</option>
      {/each}
    </select>
    <slot />
  </div>
</div>

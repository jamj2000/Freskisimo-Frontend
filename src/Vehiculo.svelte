<script>
  export let vehiculo = {};
  import { onMount } from "svelte";
</script>

<div class="card border-secondary shadow">
  <div class="card-body">
    <div class="input-group mb-3">
      <span class="input-group-text" id="license">License plate</span>
      <input
        type="text"
        class="form-control"
        aria-label="License"
        aria-describedby="license"
        bind:value={vehiculo.matricula}
      />
    </div>

    <div class="input-group mb-3">
      <span class="input-group-text" id="brand">Brand</span>
      <input
        type="text"
        class="form-control"
        aria-label="Brand"
        aria-describedby="brand"
        bind:value={vehiculo.marca}
      />
    </div>

    <div class="input-group mb-3">
      <span class="input-group-text" id="model">Model</span>
      <input
        type="text"
        class="form-control"
        aria-label="Model"
        aria-describedby="model"
        bind:value={vehiculo.modelo}
      />
    </div>

    <div class="input-group mb-3">
      <span class="input-group-text" id="registration">Registration</span>
      <span class="input-group-text" id="textRegistration">
        {vehiculo.fechaMatriculacion !== undefined
          ? vehiculo.fechaMatriculacion.slice(0, 10)
          : "Insert below"}
      </span>
    </div>

    <div class="input-group mb-3">
      <input
        type="text"
        class="form-control"
        aria-label="Registration"
        aria-describedby="registration"
        bind:value={vehiculo.fechaMatriculacion}
      />
    </div>

    <slot />
  </div>
</div>

<script>
  import { Link } from "svelte-routing";
</script>

<ul class="nav nav-tabs justify-content-center" role="tablist">
  <li class="nav-item" role="tab">
    <Link to="/" class="nav-link" onclick:active>Inicio</Link>
  </li>
  <li class="nav-item" role="tab">
    <Link to="/congelados" class="nav-link" onclick:active>Congelados</Link>
  </li>
  <li class="nav-item" role="tab">
    <Link to="/vehiculos" class="nav-link" onclick:active>Vehículos</Link>
  </li>
  <li class="nav-item" role="tab">
    <Link to="/repartidores" class="nav-link" onclick:active>Repartidores</Link>
  </li>
</ul>

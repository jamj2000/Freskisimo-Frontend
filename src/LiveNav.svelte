<script>
  import { Link } from "svelte-routing";

  export let to = "";

  function getProps({ location, href, isPartiallyCurrent, isCurrent }) {
    const isActive = href === "/" ? isCurrent : isPartiallyCurrent || isCurrent;

    // The object returned here is spread on the anchor element's attributes
    if (isActive) {
      return { class: "nav-link active" };
    }
    return { class: "nav-link" };
  }
</script>

<ul class="nav nav-tabs justify-content-center" role="tablist">
  <li class="nav-item" role="tab">
    <Link to="/" {getProps}>Inicio</Link>
  </li>
  <li class="nav-item" role="tab">
    <Link to="/congelados" {getProps}>Congelados</Link>
  </li>
  <li class="nav-item" role="tab">
    <Link to="/vehiculos" {getProps}>Vehículos</Link>
  </li>
  <li class="nav-item" role="tab">
    <Link to="/repartidores" {getProps}>Repartidores</Link>
  </li>
</ul>

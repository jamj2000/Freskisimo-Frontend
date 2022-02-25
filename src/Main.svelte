<script>
  import { Route, Link } from "svelte-routing";
  import Index from "./Index.svelte";
  import LiveNav from "./LiveNav.svelte";
  import Congelados from "./Congelados.svelte";
  import Vehiculos from "./Vehiculos.svelte";
  import Repartidores from "./Repartidores.svelte";
</script>

<main>
  <div class="container bg-light p-4">
    <LiveNav />
    <Route path="/" component={Index} />
    <Route path="/congelados" component={Congelados} />
    <Route path="/vehiculos" component={Vehiculos} />
    <Route path="/repartidores" component={Repartidores} />
  </div>
</main>
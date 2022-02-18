<script>
  import { Router } from "svelte-routing";
  import Header from "./Header.svelte";
  import Main from "./Main.svelte";

  import { setContext } from "svelte";

  const URL = {
    congelados: "https://freskisimo-app.herokuapp.com/api/congelados/",
    vehiculos: "https://freskisimo-app.herokuapp.com/api/vehiculos/",
    repartidores: "https://freskisimo-app.herokuapp.com/api/repartidores/",
  };

  setContext("URL", URL);
</script>

<Router>
  <Header />
  <Main />
</Router>

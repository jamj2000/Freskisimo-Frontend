<script>
 import { Route, Link} from "svelte-routing";
  import Index from "./Index.svelte";
  import LiveNav from "./LiveNav.svelte";
  import Congelados from "./Congelados.svelte";
</script>

<main>
	<LiveNav />
  <Route path="/" component={Index} />
  <Route path="/congelados" component={Congelados} />
</main>

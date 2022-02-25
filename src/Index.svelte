<script>
  import { Link } from "svelte-routing";
</script>

<h1 class="mt-2">Freskisimo Frontend</h1>
<p>
  <small>
    <b>Progressive Web App (PWA)</b>
  </small>
</p>
<p>
  <small>
    Backend in
    <a href="https://freskisimo-app.herokuapp.com/">
      https://freskisimo-app.herokuapp.com/
    </a>
  </small>
</p>
<p>This SPA (Single Page Application) offers 3 options:</p>

<div class="bloque">
  <Link to="/">
    <div class="resumen">
      <span class="opcion">Index</span>
      <span class="descripcion">This info.</span>
    </div>
  </Link>

  <Link to="/congelados">
    <div class="resumen">
      <span class="opcion">Congelados</span>
      <span class="descripcion"> CRUD operation with "Congelados" </span>
    </div>
  </Link>

  <Link to="/vehiculos">
    <div class="resumen">
      <span class="opcion">Vehiculos</span>
      <span class="descripcion"> CRUD operation with "Vehiculos" </span>
    </div>
  </Link>

  <Link to="/repartidores">
    <div class="resumen">
      <span class="opcion">Repartidores</span>
      <span class="descripcion"> CRUD operation with "Repartidores" </span>
    </div>
  </Link>
</div>
<p>
  <small>
    <b>
      Source code:
      <a href="https://github.com/Deg42/Freskisimo-Frontend">
        https://github.com/Deg42/Freskisimo-Frontend
      </a>
    </b>
  </small>
</p>

<style>
  h1,
  div,
  p {
    padding: 3px;
  }
  div {
    padding: 30px;
  }
  .bloque {
    display: flex;
    flex-direction: column;
  }
  .resumen {
    display: flex;
    flex-wrap: wrap;
    padding: 5px;
    margin: 0 0 15px;
    border: 1px solid #000;
    border-radius: 4px;
    box-shadow: 0 0 3px rgba(0, 0, 0, 0.19);
    border: 1px solid rgb(31, 149, 245);
    border-radius: 4px;
  }
  .opcion {
    display: flex;
    word-break: break-word;
    padding: 0 10px;
    font-size: 14px;
    font-weight: 700;
    text-shadow: 0 1px 0 rgba(0, 0, 0, 0.1);
    font-family: sans-serif;
    color: #3b4151;
    border-radius: 4px;
    background: #70cff5;
    min-width: 140px;
    padding: 10px;
  }
  .descripcion {
    font-size: 14px;
    flex: 1 1 auto;
    word-break: break-word;
    font-family: sans-serif;
    color: #3b4151;
    padding-top: 10px;
    padding-left: 10px;
  }
</style>

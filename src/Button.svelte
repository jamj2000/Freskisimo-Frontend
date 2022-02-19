<script>
  import { onMount, getContext } from "svelte";
  import { jsonData } from "./store";

  export let type = "";
  export let collection = "";
  export let document = {};

  let URL = getContext("URL");

  let addedClass = "insert";
  let handler = () => {};
  let url = "";

  function insertAction() {
    fetch(URL.congelados, {
      method: "POST",
      headers: { "Content-type": "application/json" },
      body: JSON.stringify(document),
    })
      .then((response) => response.json())
      .then((data) => ($jsonData = [...$jsonData, data]));
  }

  function updateAction() {
    fetch(url + document._id, {
      method: "PUT",
      headers: { "Content-type": "application/json" },
      body: JSON.stringify(document),
    }).then((response) => response.json());
  }

  function deleteAction() {
    fetch(url + document._id, { method: "DELETE" })
      .then((response) => response.json())
      .then(
        (data) => ($jsonData = $jsonData.filter((x) => x._id !== document._id))
      );
  }

  onMount(() => {
    switch (type) {
      case "insert":
        addedClass = "btn btn-green insert";
        handler = insertAction;
        break;
      case "update":
        addedClass = "btn btn-blue update";
        handler = updateAction;
        break;
      case "delete":
        addedClass = "btn btn-danger delete";
        handler = deleteAction;
        break;
      default:
        addedClass = "insert";
        break;
    }

    switch (collection) {
      case "congelados":
        url = URL.congelados;
        break;
      case "vehiculos":
        url = URL.vehiculos;
        break;
      case "repartidores":
        url = URL.repartidores;
        break;
      default:
        break;
    }
  });
</script>

<button class={addedClass} on:click={handler} />

<style>
  .btn-green {
    background-color: #10a35e;
  }
  .btn-blue {
    background-color: #2563c0;
  }
  .btn-red {
    background-color: #df3647;
  }
  
  .insert::after {
    content: "Insert";
  }

  .update::after {
    content: "Update";
  }

  .delete::after {
    content: "Delete";
  }
</style>

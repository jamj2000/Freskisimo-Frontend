<script>
    import { onMount, getContext } from "svelte";

    export let type = "";
    export let collection = "";
    export let document = {};

    let URL = getContext("URL");

    let addedClass = "insert";
    let handler = () => {};
    let url = "";

    function insertAction() {console.log("Insert")}
    function updateAction() {console.log("Update")}
    function deleteAction() {fetch(url + document._id, { method: "DELETE" })
            .then((response) => response.json())
            .then((data) => console.log(data));}

    onMount(() => {
        switch (type) {
            case "insert":
            addedClass = "insert";
                handler = insertAction;
                break;
            case "update":
            addedClass = "update";
                handler = updateAction;
                break;
            case "delete":
            addedClass = "delete";
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
    .insert {
        background-color: lightgreen;
    }
    .insert::after {
        content: "Insert";
    }

    .update {
        background-color: lightskyblue;
    }
    .update::after {
        content: "Update";
    }

    .delete {
        background-color: lightcoral;
    }
    .delete::after {
        content: "Delete";
    }
</style>
<script>
  import { marked } from "marked";
  import { onMount } from "svelte";

  $: EstructuraCosto = "";
  $: FlujoIngresos = "";

  onMount(async () => {
    EstructuraCosto = await (
      await fetch("Markdown/Estructura de costos.md")
    ).text();
    FlujoIngresos = await (await fetch("Markdown/Flujo de ingresos.md")).text();
  });
</script>

<section>
  <div style="background-color: greenyellow;">
    {@html EstructuraCosto != "" ? marked.parse(EstructuraCosto) : "Cargando"}
  </div>
  <div style="background-color: pink;">
    {@html EstructuraCosto != "" ? marked.parse(EstructuraCosto) : "Cargando"}
  </div>
</section>

<style>
  section {
    display: grid;
    grid-template-columns: 50% 50%;
  }
  div {
    border: 1px solid black;
    padding: 5px;
  }
</style>

<script>
  import { onMount } from "svelte";
  import { marked } from "marked";
  import Pilar from "./Pilar.svelte";

  $: PropuestaMD = "";
  $: Canales = "";
  $: SociosClave = "";
  $: ActividadesClave = "";
  $: SegmentosCliente = "";
  $: RecursosClave = "";
  $: RelacionClientes = "";

  onMount(async () => {
    PropuestaMD = await (await fetch("Markdown/Propuesta de valor.md")).text();
    Canales = await (await fetch("Markdown/Canales.md")).text();
    SociosClave = await (await fetch("Markdown/Socios clave.md")).text();
    RecursosClave = await (await fetch("Markdown/Recursos clave.md")).text();
    RelacionClientes = await (
      await fetch("Markdown/Relacion con clientes.md")
    ).text();
    SegmentosCliente = await (
      await fetch("Markdown/Segmentos de clientes.md")
    ).text();
    ActividadesClave = await (
      await fetch("Markdown/Actividades clave.md")
    ).text();
  });
</script>

<section>
  <div style="background-color: red;">
    {@html marked.parse(SociosClave ?? "")}
  </div>
  <Pilar>
    <div style="background-color: gray;">
      {@html marked.parse(ActividadesClave ?? "")}
    </div>
    <div style="background-color: pink;">
      {@html marked.parse(RelacionClientes ?? "")}
    </div>
  </Pilar>
  <div style="background-color: green;">
    {@html marked.parse(PropuestaMD ?? "")}
  </div>
  <Pilar>
    <div style="background-color: pink;">
      {@html marked.parse(RecursosClave ?? "")}
    </div>
    <div style="background-color: gray;">
      {@html marked.parse(Canales ?? "")}
    </div>
  </Pilar>
  <div style="background-color: cyan;">
    {@html marked.parse(SegmentosCliente ?? "")}
  </div>
</section>

<style>
  section {
    display: grid;
    grid-template-columns: repeat(5, 20%);
  }
  div {
    padding: 5px 25px;
    border: 1px solid black;
  }
</style>

<script>
  import BottomSide from "../components/BottomSide.svelte";
  import TopSide from "../components/TopSide.svelte";

  let screenSize = 0;
</script>

<svelte:window bind:innerWidth={screenSize} />
<main
  style="width: {screenSize < 1200 ? '1200px' : null}; 
  height: {screenSize < 1200 ? '800px' : null};
  scale:{screenSize < 1200 ? '95%' : '100%'}"
>
  <TopSide />
  <BottomSide />
</main>

<style>
  main {
    height: 95vh;
    width: 95vw;
    margin: 1vh auto;
    margin-bottom: 25px;
    border: 3px solid black;
    display: grid;
    grid-template-rows: 70% 30%;
  }
</style>

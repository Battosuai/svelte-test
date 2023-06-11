<script lang="ts">
  import Counter from "./lib/Counter.svelte";
  import CounterProp from "./lib/CounterProp.svelte";

  const obj = {
    power: 43,
    name: "Don",
    value: "go",
  };
</script>

<main class="container">
  <h1>Vite + Svelte</h1>

  <div>
    <Counter />
  </div>

  <div>
    <CounterProp />
    <CounterProp {...obj} />
  </div>
</main>

<style>
  .container {
    min-width: 100vw;
  }
</style>

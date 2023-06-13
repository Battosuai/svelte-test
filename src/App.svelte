<script lang="ts">
  import Counter from "./lib/Counter.svelte";
  import CounterProp from "./lib/CounterProp.svelte";
  import Condition from "./lib/Condition.svelte";
  import Events from "./lib/Events.svelte";
  import Inner from "./lib/Inner.svelte";
  import Binding from "./lib/Binding.svelte";

  const obj = {
    power: 43,
    name: "Don",
    value: "go",
  };

  function handleMessage(event) {
    alert(event.detail.text);
  }
</script>

<main class="container">
  <h1>Vite + Svelte</h1>

  <div>
    <Binding />
  </div>

  <div>
    <Counter />
  </div>

  <div>
    <CounterProp />
    <CounterProp {...obj} />
    <Condition />
  </div>

  <div>
    <Events />
  </div>

  <!-- on:message event directive without a value means 'forward all message events'. -->
  <!-- ex: <Inner on:message/> -->
  <!-- it works for dom event too -->
  <Inner on:message={handleMessage} />
</main>

<style>
  .container {
    min-width: 100vw;
  }
</style>

<script lang="ts">
  import { count } from "./Store";
  import { time, elapsed } from "./Time";

  function decrement() {
    count.update((n) => n - 1);
  }

  function increment() {
    count.update((n) => n + 1);
  }

  function reset() {
    count.set(0);
  }

  const formatter = new Intl.DateTimeFormat("en", {
    hour12: true,
    hour: "numeric",
    minute: "2-digit",
    second: "2-digit",
  });
</script>

<button on:click={decrement}>-</button>
<button on:click={increment}>+</button>
<button on:click={reset}>Reset</button>

<h1>The time is {formatter.format($time)}</h1>

<p>
  This page has been open for
  {$elapsed}
  {$elapsed === 1 ? "second" : "seconds"}
</p>

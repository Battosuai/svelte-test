<script lang="ts">
  import { onDestroy } from "svelte";
  import { count } from "./Store";
  import StorePractise2 from "./StorePractise2.svelte";

  let countValue = 0;

  const unsubscribe = count.subscribe((value) => {
    countValue = value;
  });

  onDestroy(() => unsubscribe());

  //can use store variables with $ sign such as $count anywhere
</script>

<h1>Count is {countValue}</h1>
<br />

<StorePractise2 />

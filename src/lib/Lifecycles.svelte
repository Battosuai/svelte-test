<script lang="ts">
  import { onMount, onDestroy, beforeUpdate, afterUpdate, tick } from "svelte";

  let photos = [];

  onMount(async () => {
    const res = await fetch(`/tutorial/api/album`);
    photos = await res.json();
  });

  let counter = 0;
  const interval = setInterval(() => (counter += 1), 1000);

  onDestroy(() => clearInterval(interval));

  let div;
  let autoscroll;

  beforeUpdate(() => {
    autoscroll =
      div && div.offsetHeight + div.scrollTop > div.scrollHeight - 20;
  });

  afterUpdate(() => {
    if (autoscroll) div.scrollTo(0, div.scrollHeight);
  });

  //   await tick();
</script>

<h1>Photo album</h1>

<div class="photos">
  {#each photos as photo}
    <figure>
      <img
        src={photo.thumbnailUrl}
        alt={photo.title}
      />
      <figcaption>{photo.title}</figcaption>
    </figure>
  {:else}
    <!-- this block renders when photos.length === 0 -->
    <p>loading...</p>
  {/each}
</div>

<style>
  .photos {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    grid-gap: 8px;
  }

  figure,
  img {
    width: 100%;
    margin: 0;
  }
</style>

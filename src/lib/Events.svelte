<script lang="ts">
  let m = { x: 0, y: 0 };

  function handleMousemove(event: MouseEvent) {
    m.x = event.clientX;
    m.y = event.clientY;
    console.log(m);
  }

  function handleClick() {
    alert("no more alerts");
  }
</script>

<!-- Could be done inline too ::: <div on:mousemove="{e => m = { x: e.clientX, y: e.clientY }}"></div> -->
<div on:mousemove={handleMousemove}>
  <h1>Events Stuff</h1>

  <!-- Once modifier runs a single time -->
  <button on:click|once={handleClick}> Click me </button>
</div>

<!-- Event Modifiers:::
preventDefault
stopPropagation
passive
nonpassive
capture
once
self
trusted

Can chain like this ::: on:click|once|capture={...} -->

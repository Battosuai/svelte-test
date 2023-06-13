<script lang="ts">
  let a: number = 2;
  let b: number = 2;
  let yes: boolean = true;

  let scoops: number = 1;
  let flavours: string[] = ["Mint choc chip"];

  let html = "<h2>Hello World</h2>";

  let canvas;

  $: {
    console.log(scoops);
  }

  $: {
    console.log(flavours);
  }
</script>

<h1>Bindings</h1>

<input
  type="number"
  bind:value={a}
/>

<input
  type="range"
  bind:value={a}
  min={0}
  max={10}
/>

<input
  type="checkbox"
  bind:checked={yes}
/>

<label>
  <input
    type="radio"
    bind:group={scoops}
    name="scoops"
    value={1}
  />
  One scoop
</label>

<label>
  <input
    type="radio"
    bind:group={scoops}
    name="scoops"
    value={2}
  />
  Two scoops
</label>

<label>
  <input
    type="radio"
    bind:group={scoops}
    name="scoops"
    value={3}
  />
  Three scoops
</label>

<label>
  <input
    type="checkbox"
    bind:group={flavours}
    name="flavours"
    value="Cookies and cream"
  />
  Cookies and cream
</label>

<label>
  <input
    type="checkbox"
    bind:group={flavours}
    name="flavours"
    value="Mint choc chip"
  />
  Mint choc chip
</label>

<label>
  <input
    type="checkbox"
    bind:group={flavours}
    name="flavours"
    value="Raspberry ripple"
  />
  Raspberry ripple
</label>

<select
  multiple
  bind:value={flavours}
>
  {#each flavours as flavour}
    <option value={flavour}>
      {flavour}
    </option>
  {/each}
</select>

<div
  contenteditable="true"
  bind:innerHTML={html}
/>

<!-- The complete set of bindings for <audio> and <video> is as follows — six readonly bindings...

    duration (readonly) — the total duration of the video, in seconds
    buffered (readonly) — an array of {start, end} objects
    seekable (readonly) — ditto
    played (readonly) — ditto
    seeking (readonly) — boolean
    ended (readonly) — boolean
    ...and five two-way bindings:
    
    currentTime — the current point in the video, in seconds
    playbackRate — how fast to play the video, where 1 is 'normal'
    paused — this one should be self-explanatory
    volume — a value between 0 and 1
    muted — a boolean value where true is muted
    Videos additionally have readonly videoWidth and videoHeight bindings. -->

<!-- The readonly this binding applies to every element (and component) and allows you to obtain a reference to rendered elements. For example, we can get a reference to a <canvas> element: -->
<canvas
  bind:this={canvas}
  width={32}
  height={32}
/>
<!-- value of canvas will be undefined until the component has mounted, so we put the logic inside the onMount lifecycle function. -->

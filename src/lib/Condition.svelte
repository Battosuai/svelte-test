<script lang="ts">
  let user = { loggedIn: false };

  function toggle() {
    user.loggedIn = !user.loggedIn;
  }

  let cats = [
    { id: "J---aiyznGQ", name: "Keyboard Cat" },
    { id: "z_AbfPXTKms", name: "Maru" },
    { id: "OUtn3pvWmpg", name: "Henri The Existential Cat" },
  ];
</script>

<!-- # block opening. / block end, : block continuation -->
{#if !user.loggedIn}
  <button on:click={toggle}>Log In</button>
{/if}

{#if user.loggedIn}
  <button on:click={toggle}>Log Out</button>
{/if}

{#if !user.loggedIn}
  <button on:click={toggle}>Log In</button>
{:else}
  <button on:click={toggle}>Log Out</button>
{/if}

<!-- for else if use :else if -->

<!-- for index there is a second argument like cat, i -->
<!-- destructuring can be used also such as cats as {id, name} -->
<!-- for key it would be cats as cat (cat.id) -->
<ul>
  {#each cats as cat}
    <li>{cat.name}</li>
  {/each}
</ul>

<!-- For async await

{#await promise}
	<p>...waiting</p>
{:then number}
	<p>The number is {number}</p>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await} -->

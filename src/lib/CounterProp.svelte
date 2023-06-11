<script lang="ts">
  export let value: string = "Not hello";

  //$$props for referencing all props
  //$$restProps contains only the props which are not declared with export
</script>

<h1>Prop Check</h1>

<span>Value: {value}</span>

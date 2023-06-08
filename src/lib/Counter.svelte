<script lang="ts">
  let name: string = "world";
  let src: string = "https://picsum.photos/200/300";
</script>

<h1>Hello {name.toUpperCase()}</h1>

<img
  {src}
  alt="lorem picsum"
/>

<style>
  img {
    height: 200px;
    width: 200px;
    object-fit: cover no-repeat;
  }
</style>

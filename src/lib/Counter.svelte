<script lang="ts">
  let name: string = "world";
  let src: string = "https://picsum.photos/200/300";
  let count: number = 0;

  $: doubled = count * 2;

  $: if (count > 10) {
    alert("Count is high");
    count = 9;
  }

  $: {
    console.log("count: ", count);
  }

  let numbers: number[] = [2, 5, 1, 7];

  function incrementCount() {
    count++;
  }

  $: {
    console.log("numbers", numbers);
  }

  function updateObject() {
    numbers.push(4);
    numbers = numbers; // Until assignment happens reactivity doesn't trigger for objects
    // Or, numbers = [...numbers,4]
  }

  let obj = {
    foo: "foo",
  };

  const foo = {
    foo: obj.foo,
    bar: "",
  };

  function updateObject2() {
    foo.bar = "baz";
    console.log(obj);
  }

  $: {
    console.log("foo", foo);
  }

  $: {
    console.log("obj", obj);
  }
</script>

<h1>Hello {name.toUpperCase()}</h1>

<img
  {src}
  alt="lorem picsum"
/>

<button on:click={incrementCount}>Click</button>
<span>{doubled}</span>

<button on:click={updateObject}>Unprimitive</button>
<button on:click={updateObject2}>Update</button>

<style>
  img {
    height: 200px;
    width: 200px;
    object-fit: cover no-repeat;
  }
</style>

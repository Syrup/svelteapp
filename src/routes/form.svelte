<script lang="ts">
  import { onMount } from "svelte";
  let name = "";
  let users = [];
  $: username = users
    ? users.find((x) => x.name.toLowercase().includes(name.toLowercase()))
    : undefined;

  onMount(async () => {
    let res = await fetch("https://jsonplaceholder.typicode.com/users");
    const data = await res.json();
    users = data;
  });

  // let promise = search(name)
  console.log(users);
</script>

<input type="search" bind:value={name} />
<p>{username}</p>

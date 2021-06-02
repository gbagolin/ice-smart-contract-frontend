<script>
  import { onMount } from "svelte";

  export let params;

  const apiUrl = "";
  let data = [];

  onMount(async () => {
    const response = await fetch(apiUrl + params.id);
    data = await response.json();
  });
</script>

{#if data.title || data.body === undefined}
  loading...
{:else}
  <h1>{data.title}</h1>
  <p>{data.body}</p>
{/if}

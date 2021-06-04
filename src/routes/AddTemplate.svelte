<script>
    import { onMount } from "svelte";
  
    export let params;
    const apiUrl = "http://localhost:7000/getSchema/";
    const CONTRACT_ADDRESS = "0x7d7360A2CfC3C3547688cc0A0285a312eFBe5d82";
    let data = undefined;
  
    onMount(async () => {
      const response = await fetch(
        apiUrl + params.privateKey + "/" + CONTRACT_ADDRESS
      );
      data = await response.json();
      console.log(data);
    });
  </script>
  
  {#if data === undefined}
    loading...
  {:else}
  ciao
  {/if}
  
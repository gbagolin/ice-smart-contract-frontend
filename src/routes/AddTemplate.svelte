<script lang="ts">
  import { onMount } from "svelte";
  import { privateKey } from "../stores/privateKey";
  import { contractAddress } from "../stores/contracAddress";
  import axios from "axios";

  export let params;

  const apiUrl = "http://localhost:7000/getSchema/";
  let data: JSON = undefined;
  const schema = params.schema;
  const schemaName =
    schema.charAt(0).toUpperCase() +
    schema.slice(1).toLowerCase();

  onMount(async () => {
    console.log(params.schema);
    const response = await axios.post(apiUrl, {
      schema: params.schema,
    });
    data = response.data;
    console.log(data);
  });
</script>

{#if data === undefined}
  loading...
{:else}
  <main class="flex justify-center items-center">
    <div class="my-40" />
    <div class="grid grid-cols-1 gap-10">
      <div class="flex justify-center">
        <h1 class="text-6xl font-bold">
          Add {schemaName}
        </h1>
      </div>
      {#each Object.keys(data) as name}
        <div>
          <input
            class="w-96 h-10 rounded-lg border-2 border-black text-center text-lg italic"
            placeholder={"Insert " +
              name.charAt(0).toUpperCase() +
              name.slice(1).toLowerCase()}
            contenteditable="true"
          />
        </div>
      {/each}
      <div>
        <button
          class="bg-black 
      hover:bg-gray-500 
      text-white 
      font-bold 
      w-96 h-10
      rounded-lg 
      cursor-pointer">Add {schemaName}</button
        >
      </div>
    </div>
  </main>
{/if}

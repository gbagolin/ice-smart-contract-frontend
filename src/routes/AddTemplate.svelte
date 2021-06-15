<script lang="ts">
  import { onMount } from "svelte";
  import { privateKey } from "../stores/privateKey";
  import axios from "axios";
  import { BASE_API_URL } from "../stores/baseApiName";

  export let params;

  const apiUrl = BASE_API_URL + "/getSchema";
  let data: JSON = undefined;

  const schema: string = params.schema;
  const schemaName: string =
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

  const MENU_URL = `/menu/${$privateKey}`;

  const elementToAdd = {};
  let id = undefined;

  async function sendPost() {
    console.log($privateKey);
    const URL = `${BASE_API_URL}/add${schema}`;
    elementToAdd["privateKey"] = $privateKey;
    console.log(elementToAdd);
    const response = await axios.post(URL, elementToAdd);
    console.log(response);
    id = response.data.id;
    // window.location.href = `/menu/${privateKey}`;
  }
</script>

{#if data === undefined}
  loading...
{:else}
  <div class="mt-40" />
  <main class="flex justify-center">
    <div class="grid grid-cols-1 gap-10">
      <div class="flex justify-center">
        <a
          href={MENU_URL}
          class="font-bold text-lg"
          >Back to menu</a
        >
      </div>
      <div class="flex justify-center">
        <h1 class="text-6xl font-bold">
          Add {schemaName.replace("_", " ")}
        </h1>
      </div>
      {#each Object.keys(data) as name}
        {#if name !== "id"}
          <div class="flex justify-center">
            <input
              class="w-96 h-10 rounded-lg border-2 border-black text-center text-lg italic"
              placeholder={"Insert " +
                name.charAt(0).toUpperCase() +
                name.slice(1).toLowerCase()}
              contenteditable="true"
              bind:value={elementToAdd[name]}
            />
          </div>
        {:else}{/if}
      {/each}
      <div class="flex justify-center">
        <button
          class=" 
                  font-bold 
                  text-lg
                  cursor-pointer"
          on:click={() => sendPost()}
          >Add {schemaName}
        </button>
      </div>

      {#if id != undefined}
        <div
          class="bg-green-100 py-5 text-center text-xl rounded-2xl"
        >
          {schemaName}'s id : {id}
        </div>
      {/if}
    </div>
  </main>
{/if}

<script lang="ts">
  import { onMount } from "svelte";
  import { payload } from "../stores/objectToGet";
  import { privateKey } from "../stores/privateKey";
  import axios from "axios";
  import { BASE_API_URL } from "../stores/baseApiName";
  import { each } from "svelte/internal";

  export let params;

  const MENU_URL = `/menu/${$privateKey}`;
  const API = `${BASE_API_URL}/get${params.schema}/${$privateKey}/${$payload["id"]}`;
  let data: JSON = undefined;

  onMount(async () => {
    console.log("API: ", API);
    console.log(params.schema);
    const response = await axios.get(API);
    data = response.data;
    console.log(response.data);
  });

  const schema: string = params.schema;
  const schemaName: string =
    schema.charAt(0).toUpperCase() +
    schema.slice(1).toLowerCase();
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
          class="text-4xl underline text-blue-500"
          >Back to menu</a
        >
      </div>
      <div class="flex justify-center">
        <h1 class="text-6xl font-bold">
          {schemaName} Information
        </h1>
      </div>

      <div class="flex flex-col justify-center">
        {#each Object.keys(data) as key}
          <div class="text-2xl">
            {key} : {data[key]}
          </div>
        {/each}
      </div>
    </div>
  </main>
{/if}

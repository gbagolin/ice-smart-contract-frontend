<script lang="ts">
  import { onMount } from "svelte";
  import { payload } from "../stores/objectToGet";
  import { privateKey } from "../stores/privateKey";
  import axios from "axios";
  import { BASE_API_URL } from "../stores/baseApiName";
  import { each } from "svelte/internal";
  import { menu } from "../stores/menuStore";

  export let params;

  const MENU_URL = `${$menu}`;
  const API = `${BASE_API_URL}/get${params.schema}/${$privateKey}/${$payload["id"]}`;
  let data: JSON = undefined;

  function flattenObject(ob) {
    var toReturn = {};

    for (var i in ob) {
      if (!ob.hasOwnProperty(i)) continue;

      if (typeof ob[i] == "object" && ob[i] !== null) {
        var flatObject = flattenObject(ob[i]);
        for (var x in flatObject) {
          if (!flatObject.hasOwnProperty(x)) continue;

          toReturn[i + "." + x] = flatObject[x];
        }
      } else {
        toReturn[i] = ob[i];
      }
    }
    return toReturn;
  }

  onMount(async () => {
    console.log("API: ", API);
    console.log(params.schema);
    const response = await axios.get(API);
    data = flattenObject(response.data);
    // data = response.data;
    console.log(response.data);
  });

  const schema: string = params.schema;
  const schemaName: string = schema
    .match(/[A-Z][a-z]+/g)
    .join(" ");
  console.log("Schema name: ", schemaName);
</script>

{#if data === undefined}
  loading...
{:else}
  <div class="mt-40" />
  <main class="flex justify-center">
    <div class="grid grid-cols-1 gap-10">
      <div class="flex justify-center">
        <a href={MENU_URL} class="font-bold text-lg"
          >Back to menu</a
        >
      </div>
      <div class="flex justify-center">
        <h1 class="text-6xl font-bold">
          {schemaName} Data
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

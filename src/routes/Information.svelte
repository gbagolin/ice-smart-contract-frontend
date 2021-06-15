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
    // data = flattenObject(response.data);
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
        <a href={MENU_URL} class="font-bold text-lg"
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
            {#if typeof data[key] === "object"}
              {#each Object.keys(data[key]) as childKey}
                {#if typeof data[key][childKey] === "object"}
                  {#each Object.keys(data[key][childKey]) as childChildKey}
                    {childChildKey} : {data[key][childKey][
                      childChildKey
                    ]}{/each}
                {:else}
                  {childKey} : {data[key][childKey]}
                {/if}
              {/each}
            {/if}
          </div>
        {/each}
      </div>
    </div>
  </main>
{/if}

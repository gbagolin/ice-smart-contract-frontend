<script lang="ts">
  import { onMount } from "svelte";
  import { privateKey } from "../stores/privateKey";
  import { contractAddress } from "../stores/contracAddress";

  const API_URL = "http://localhost:7000/loadContract/";
  let data: object = undefined;

  let schemaToQuery: String;

  onMount(async () => {
    console.log($privateKey);
    const response = await fetch(
      API_URL + $privateKey + "/" + $contractAddress
    );
    data = await response.json();
    console.log(data);
  });

  function setSchemaToQuery(schema: String) {
    schemaToQuery = schema;
  }
</script>

{#if data === undefined}
  loading...
{:else}
  <main>
    <div class="flex flex-col h-screen items-center">
      <div class="mt-20">
        <div class="grid grid-cols-3 gap-10">
          <div class="col-span-3">
            <h1 class="text-6xl font-bold">
              Choose an action
            </h1>
          </div>
          <div>
            <p class="text-2xl items-center">Company:</p>
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a
              on:click={() => setSchemaToQuery("COMPANY")}
              href="/add/{schemaToQuery}">Add Company</a
            >
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a
              on:click={() => setSchemaToQuery("COMPANY")}
              href="/get/{schemaToQuery}">Get Company</a
            >
          </div>
          <div>
            <p class="text-2xl">Machine:</p>
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a
              on:click={() => setSchemaToQuery("MACHINE")}
              href="/add/{schemaToQuery}">Add Machine</a
            >
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a
              on:click={() => setSchemaToQuery("MACHINE")}
              href="/get/{schemaToQuery}">Get Machine</a
            >
          </div>
          <div>
            <p class="text-2xl">Recipe:</p>
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a
              on:click={() => setSchemaToQuery("RECIPE")}
              href="/add/{schemaToQuery}">Add Recipe</a
            >
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a
              on:click={() => setSchemaToQuery("RECIPE")}
              href="/get/{schemaToQuery}">Get Recipe</a
            >
          </div>
          <div>
            <p class="text-2xl">Recipe step:</p>
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a
              on:click={() =>
                setSchemaToQuery("RECIPE_STEP")}
              href="/add/{schemaToQuery}">Add Recipe step</a
            >
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a
              on:click={() =>
                setSchemaToQuery("RECIPE_STEP")}
              href="/get/{schemaToQuery}">Get Recipe step</a
            >
          </div>
          <div>
            <p class="text-2xl">Measure Constraint:</p>
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a
              on:click={() =>
                setSchemaToQuery("MEASURE_CONSTRAINT")}
              href="/add/{schemaToQuery}"
              >Add Measure Constraint</a
            >
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a
              on:click={() =>
                setSchemaToQuery("MEASURE_CONSTRAINT")}
              href="/get/{schemaToQuery}"
              >Get Measure Constraint</a
            >
          </div>
          <div>
            <p class="text-2xl">Products</p>
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a
              on:click={() => setSchemaToQuery("PRODUCT")}
              href="/add/{schemaToQuery}">Add Product</a
            >
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a 
            on:click={() => setSchemaToQuery("PRODUCT")}
            href="/get/{schemaToQuery}"
              >Get Product Information</a
            >
          </div>
          <div>
            <p class="text-2xl">Phase</p>
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a
              on:click={() => setSchemaToQuery("PHASE")}
              href="/add/{schemaToQuery}">Add Phase</a
            >
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a 
            on:click={() => setSchemaToQuery("PHASE")}
            href="/get/{schemaToQuery}">Get Phase</a>
          </div>
          <div>
            <p class="text-2xl">Measure</p>
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a
              on:click={() => setSchemaToQuery("MEASURE")}
              href="/add/{schemaToQuery}">Add Measure</a
            >
          </div>
          <div
            class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
          >
            <a 
            on:click={() => setSchemaToQuery("MEASURE")}
            href="/get/{schemaToQuery}">Get Measure</a>
          </div>
        </div>
      </div>
    </div>
  </main>
{/if}

<script lang="ts">
  let schemaToQuery: String;

  import { privateKey } from "../stores/privateKey";

  function setSchemaToQuery(schema: String) {
    schemaToQuery = schema;
    console.log($privateKey);
  }
</script>

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
            on:click={() => setSchemaToQuery("Company")}
            href="/add/{schemaToQuery}">Add Company</a
          >
        </div>
        <div
          class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
        >
          <a
            on:click={() => setSchemaToQuery("Company")}
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
            on:click={() => setSchemaToQuery("Machine")}
            href="/add/{schemaToQuery}">Add Machine</a
          >
        </div>
        <div
          class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
        >
          <a
            on:click={() => setSchemaToQuery("Machine")}
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
            on:click={() => setSchemaToQuery("Recipe")}
            href="/add/{schemaToQuery}">Add Recipe</a
          >
        </div>
        <div
          class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
        >
          <a
            on:click={() => setSchemaToQuery("Recipe")}
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
            on:click={() => setSchemaToQuery("RecipeStep")}
            href="/add/{schemaToQuery}">Add Recipe step</a
          >
        </div>
        <div
          class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
        >
          <a
            on:click={() => setSchemaToQuery("RecipeStep")}
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
              setSchemaToQuery("MeasureConstraint")}
            href="/add/{schemaToQuery}"
            >Add Measure Constraint</a
          >
        </div>
        <div
          class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
        >
          <a
            on:click={() =>
              setSchemaToQuery("MeasureConstraint")}
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
            on:click={() => setSchemaToQuery("Product")}
            href="/add/{schemaToQuery}">Add Product</a
          >
        </div>
        <div
          class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
        >
          <a
            on:click={() => setSchemaToQuery("Product")}
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
            on:click={() => setSchemaToQuery("Phase")}
            href="/add/{schemaToQuery}">Add Phase</a
          >
        </div>
        <div
          class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
        >
          <a
            on:click={() => setSchemaToQuery("Phase")}
            href="/get/{schemaToQuery}">Get Phase</a
          >
        </div>
        <div>
          <p class="text-2xl">Measure</p>
        </div>
        <div
          class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
        >
          <a
            on:click={() => setSchemaToQuery("Measure")}
            href="/add/{schemaToQuery}">Add Measure</a
          >
        </div>
        <div
          class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200 text-center"
        >
          <a
            on:click={() => setSchemaToQuery("Measure")}
            href="/get/{schemaToQuery}">Get Measure</a
          >
        </div>
      </div>
    </div>
  </div>
</main>

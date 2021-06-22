<script lang="ts">
import { menu } from "../stores/menuStore";

  let schemaToQuery: String;

  import { privateKey } from "../stores/privateKey";

  function setSchemaToQuery(schema: String) {
    schemaToQuery = schema;
    console.log($privateKey);
    menu.set("/menuGeneralUser/");
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
        <div class="">
          <a
            on:click={() => setSchemaToQuery("Company")}
            href="/add/{schemaToQuery}"
            class="flex py-2 px-2 font-bold">Add Company</a
          >
        </div>
        <div class="">
          <a
            on:click={() => setSchemaToQuery("Company")}
            href="/get/{schemaToQuery}"
            class="flex py-2 px-2 font-bold">Get Company</a
          >
        </div>
        <div>
          <p class="text-2xl">Machine:</p>
        </div>
        <div class="">
          <a
            on:click={() => setSchemaToQuery("Machine")}
            href="/add/{schemaToQuery}"
            class="flex py-2 px-2 font-bold">Add Machine</a
          >
        </div>
        <div class="">
          <a
            on:click={() => setSchemaToQuery("Machine")}
            href="/get/{schemaToQuery}"
            class="flex py-2 px-2 font-bold">Get Machine</a
          >
        </div>
        <div>
          <p class="text-2xl">Recipe:</p>
        </div>
        <div class="">
          <a
            on:click={() => setSchemaToQuery("Recipe")}
            href="/add/{schemaToQuery}"
            class="flex py-2 px-2 font-bold">Add Recipe</a
          >
        </div>
        <div class="">
          <a
            on:click={() => setSchemaToQuery("Recipe")}
            href="/get/{schemaToQuery}"
            class="flex py-2 px-2 font-bold">Get Recipe</a
          >
        </div>
        <div>
          <p class="text-2xl">Recipe step:</p>
        </div>
        <div class="">
          <a
            on:click={() => setSchemaToQuery("RecipeStep")}
            href="/add/{schemaToQuery}"
            class="flex py-2 px-2 font-bold"
            >Add Recipe step</a
          >
        </div>
        <div class="">
          <a
            on:click={() => setSchemaToQuery("RecipeStep")}
            href="/get/{schemaToQuery}"
            class="flex py-2 px-2 font-bold"
            >Get Recipe step</a
          >
        </div>
        <div>
          <p class="text-2xl">Measure Constraint:</p>
        </div>
        <div class="">
          <a
            on:click={() =>
              setSchemaToQuery("MeasureConstraint")}
            href="/add/{schemaToQuery}"
            class="flex py-2 px-2 font-bold"
            >Add Measure Constraint</a
          >
        </div>
        <div class="">
          <a
            on:click={() =>
              setSchemaToQuery("MeasureConstraint")}
            href="/get/{schemaToQuery}"
            class="flex py-2 px-2 font-bold"
            >Get Measure Constraint</a
          >
        </div>
        <div>
          <p class="text-2xl">Products</p>
        </div>
        <div class="">
          <a
            on:click={() => setSchemaToQuery("Product")}
            href="/add/{schemaToQuery}"
            class="flex py-2 px-2 font-bold">Add Product</a
          >
        </div>
        <div class="">
          <a
            on:click={() =>
              setSchemaToQuery("ProductInformation")}
            href="/get/{schemaToQuery}"
            class="flex py-2 px-2 font-bold"
            >Get Product Information</a
          >
        </div>
        <div>
          <p class="text-2xl">Phase</p>
        </div>
        <div class="">
          <a
            on:click={() => setSchemaToQuery("Phase")}
            href="/add/{schemaToQuery}"
            class="flex py-2 px-2 font-bold">Add Phase</a
          >
        </div>
        <div class="">
          <a
            on:click={() => setSchemaToQuery("Phase")}
            href="/get/{schemaToQuery}"
            class="flex py-2 px-2 font-bold">Get Phase</a
          >
        </div>
        <div>
          <p class="text-2xl">Measure</p>
        </div>
        <div class="">
          <a
            on:click={() => setSchemaToQuery("Measure")}
            href="/add/{schemaToQuery}"
            class="flex py-2 px-2 font-bold">Add Measure</a
          >
        </div>
        <div class="">
          <a
            on:click={() => setSchemaToQuery("Measure")}
            href="/get/{schemaToQuery}"
            class="flex py-2 px-2 font-bold">Get Measure</a
          >
        </div>
      </div>
    </div>
  </div>
</main>

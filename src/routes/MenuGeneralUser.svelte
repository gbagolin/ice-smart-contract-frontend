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
      <div class="grid grid-cols-2 gap-10">
        <div class="col-span-2 text-center">
          <a class="underline text-lg" href="/">
            Back to Login 
          </a>
        </div>
        <div class="col-span-2">
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
            href="/get/{schemaToQuery}"
            class="flex py-2 px-2 font-bold">Get Measure</a
          >
        </div>
      </div>
    </div>
  </div>
</main>

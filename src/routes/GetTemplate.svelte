<script lang="ts">
  import { onMount } from "svelte";
  import { privateKey } from "../stores/privateKey";
  import { contractAddress } from "../stores/contracAddress";
  import axios from "axios";

  export let params;

  const schema: string = params.schema;
  const schemaName =
    schema.charAt(0).toUpperCase() +
    schema.slice(1).toLowerCase();

  let id: string;
</script>

<main class="flex justify-center items-center">
  <div class="my-40" />
  <div class="grid grid-cols-1 gap-10">
    <div class="flex justify-center">
      <h1 class="text-6xl font-bold">
        Get {schemaName} by Id
      </h1>
    </div>
    <div>
      <input
        class="w-96 h-10 rounded-lg border-2 border-black text-center text-lg italic"
        placeholder="{schemaName}'s Id"
        contenteditable="true"
        bind:value={id}
      />
    </div>
    <div>
      <button
        class="bg-black 
        hover:bg-gray-500 
        text-white 
        font-bold 
        w-96 h-10
        rounded-lg 
        cursor-pointer">Get {schemaName} by Id</button
      >
    </div>
  </div>
</main>

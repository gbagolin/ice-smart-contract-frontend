<script lang="ts">
  import { onMount } from "svelte";
  import { privateKey } from "../stores/privateKey";
  import { contractAddress } from "../stores/contractAddress";
  import { BASE_API_URL } from "../stores/baseApiName";
  import axios from "axios";
  import { payload } from "../stores/objectToGet";
import { menu } from "../stores/menuStore";

  export let params;

  const schema: string = params.schema;
  const schemaName: string = schema
    .match(/[A-Z][a-z]+/g)
    .join(" ");
  console.log("Schema name: ", schemaName);

  let id: string;

  const MENU_URL = `${$menu}`;

  async function sendGet() {
    console.log(id);
    // const URL = `${BASE_API_URL}/get${schema}/${$privateKey}/${id}`;
    // const response = await axios.get(URL);
    payload.set({ id: id });
    console.log(`Payload: `, $payload);
    // console.log(response.data);
  }
</script>

<div class="my-40" />
<main class="flex justify-center items-center">
  <div class="grid grid-cols-1 gap-10">
    <div class="flex justify-center">
      <a href={MENU_URL} class="text-lg font-bold"
        >Back to menu</a
      >
    </div>
    <div class="flex justify-center">
      <h1 class="text-6xl font-bold">
        Get {schemaName.replace("_", " ")} by Id
      </h1>
    </div>
    <div class="flex justify-center">
      <input
        class="w-96 h-10 rounded-lg border-2 border-black text-center text-lg italic"
        placeholder="{schemaName}'s Id"
        contenteditable="true"
        bind:value={id}
      />
    </div>
    <div class="flex justify-center">
      <a
        class="font-bold
        text-lg
        cursor-pointer"
        on:click={sendGet}
        href="/information/{schema}"
        >Get {schemaName} by Id</a
      >
    </div>
  </div>
</main>

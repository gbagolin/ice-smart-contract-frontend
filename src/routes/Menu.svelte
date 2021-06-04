<script>
  import { onMount } from "svelte";

  export let params;
  const apiUrl = "http://localhost:7000/loadContract/";
  const CONTRACT_ADDRESS = "0x7d7360A2CfC3C3547688cc0A0285a312eFBe5d82";
  let data = undefined;

  onMount(async () => {
    const response = await fetch(
      apiUrl + params.privateKey + "/" + CONTRACT_ADDRESS
    );
    data = await response.json();
    console.log(data);
  });
</script>

{#if data === undefined}
  loading...
{:else}
  <main>
    <div class="flex flex-col h-screen items-center">
      <div class="mt-20">
        <div class="grid grid-cols-3 gap-10">
          <div class="col-span-3">
            <h1 class="text-6xl font-bold">Choose an action</h1>
          </div>
          <div>
            <p class="text-2xl items-center">Company:</p>
          </div>
          <div>
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Add Company</button
            >
          </div>
          <div >
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Get Company</button
            >
          </div>
          <div>
            <p class="text-2xl">Machine:</p>
          </div>
          <div>
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Add Machine</button
            >
          </div>
          <div >
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Get Machine</button
            >
          </div>
          <div>
            <p class="text-2xl">Recipe:</p>
          </div>
          <div>
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Add Recipe</button
            >
          </div>
          <div >
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Get Recipe</button
            >
          </div>
          <div>
            <p class="text-2xl">Recipe step:</p>
          </div>
          <div>
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Add Recipe step</button
            >
          </div>
          <div >
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Get Recipe step</button
            >
          </div>
          <div>
            <p class="text-2xl">Measure Constraint:</p>
          </div>
          <div>
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Add Measure Constraint</button
            >
          </div>
          <div >
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Get Measure Constraint</button
            >
          </div>
          <div>
            <p class="text-2xl">Products</p>
          </div>
          <div>
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Add Product</button
            >
          </div>
          <div>
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Get Product Information</button
            >
          </div>
          <div>
            <p class="text-2xl">Phase</p>
          </div>
          <div>
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Add Phase</button
            >
          </div>
          <div>
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Get Phase</button
            >
          </div>
          <div>
            <p class="text-2xl">Measure</p>
          </div>
          <div>
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Add Measure</button
            >
          </div>
          <div>
            <button class="border-2 border-black rounded-lg w-40 h-12 hover:bg-gray-200"
              >Get Measure</button
            >
          </div>
        </div>
      </div>
    </div>
  </main>
{/if}

<script lang="ts">
  import { privateKey } from "../stores/privateKey";

  const LOAD_CONTRACT_URL = "/menu/";
  let privateKeyString: string;
  let url: string;

  function setUrl() {
    privateKey.set(privateKeyString);
    url = LOAD_CONTRACT_URL + privateKeyString + "/";
  }
</script>

<main>
  <div class="flex flex-col items-center h-screen">
    <div class="mt-32 lg:mt-64 md:mt-48 sm:mt-48">
      <h1 class="text-8xl font-black">
        ICE Smart Contract
      </h1>
      <p class="mt-8 text-3xl text-gray-600">
        A utility to query the ICE blockchain, to get
        product information.
      </p>
    </div>
    <div class="mt-16">
      <input
        class="w-96 h-10 rounded-lg border-2 border-black text-center text-lg italic"
        placeholder="Account's private key"
        contenteditable="true"
        bind:value={privateKeyString}
      />
      <a
        class="ml-4 bg-black 
        hover:bg-gray-500 
        text-white 
        font-bold 
        py-3 px-8 
        rounded-lg 
        cursor-pointer"
        href={url}
        on:click={setUrl}>Search</a
      >
    </div>
  </div>
</main>

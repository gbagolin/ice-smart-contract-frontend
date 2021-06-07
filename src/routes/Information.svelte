<div class="mt-40" />
<main class="flex justify-center">
  <div class="grid grid-cols-1 gap-10">
    <div class="flex justify-center">
      <a class="text-4xl underline text-blue-500"
        >Back to menu</a
      >
    </div>
    <div class="flex justify-center">
      <h1 class="text-6xl font-bold">
        Add {schemaName.replace("_", " ")}
      </h1>
    </div>

    <div class="flex justify-center">
      <button
        class="bg-black 
                  hover:bg-gray-500 
                  text-white 
                  text-center
                  font-bold 
                  text-lg
                  w-96 h-10
                  rounded-lg 
                  cursor-pointer"
        on:click={() => sendPost()}
        >Add {schemaName}
      </button>
    </div>
  </div>
</main>

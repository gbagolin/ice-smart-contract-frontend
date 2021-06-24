<script lang="ts">
  import router from "page";

  // Include our Routes
  import Home from "./routes/Home.svelte";
  import Menu from "./routes/MenuAdmin.svelte";
  import AddTemplate from "./routes/AddTemplate.svelte";
  import GetTemplate from "./routes/GetTemplate.svelte";
  import Information from "./routes/Information.svelte";
  import MenuAdmin from "./routes/MenuAdmin.svelte";
  import MenuDataProvider from "./routes/MenuDataProvider.svelte";
  import MenuGeneralUser from "./routes/MenuGeneralUser.svelte";
  import MenuOwner from "./routes/MenuOwner.svelte";
  import axios from "axios";
  import { BASE_API_URL } from "./stores/baseApiName";
  import { contractAddress } from "./stores/contractAddress";
  let page;
  let params;

  (async () => {
    const response = await axios.get(
      `${BASE_API_URL}/getContractAddress`
    );
    const address = response.data["message"];
    console.log("Contract address: ", address);
    contractAddress.set(address);
  })();

  // Set up the pages to watch for
  router("/", () => (page = Home));
  router(
    "/menuAdmin/",

    // Before we set the component
    (ctx, next) => {
      params = ctx.params;
      next();
    },

    // Finally set the component
    () => (page = MenuAdmin)
  );

  router(
    "/menuDataProvider/",

    // Before we set the component
    (ctx, next) => {
      params = ctx.params;
      next();
    },

    // Finally set the component
    () => (page = MenuDataProvider)
  );

  router(
    "/menuGeneralUser/",

    // Before we set the component
    (ctx, next) => {
      params = ctx.params;
      next();
    },

    // Finally set the component
    () => (page = MenuGeneralUser)
  );

  router(
    "/menuOwner/",

    // Before we set the component
    (ctx, next) => {
      params = ctx.params;
      next();
    },

    // Finally set the component
    () => (page = MenuOwner)
  );

  router(
    "/add/:schema",

    // Before we set the component
    (ctx, next) => {
      params = ctx.params;
      next();
    },

    // Finally set the component
    () => (page = AddTemplate)
  );

  router(
    "/get/:schema",

    // Before we set the component
    (ctx, next) => {
      params = ctx.params;
      next();
    },

    // Finally set the component
    () => (page = GetTemplate)
  );

  router(
    "/information/:schema",

    // Before we set the component
    (ctx, next) => {
      params = ctx.params;
      next();
    },

    // Finally set the component
    () => (page = Information)
  );

  // Set up the router to start and actively watch for changes
  router.start();
</script>

<svelte:component this={page} {params} />

<style global>
  @tailwind base;
  @tailwind components;
  @tailwind utilities;

  element {
    --eth-light-blue: rgb(72, 203, 217);
    --eth-light-light-blue: rgb(121, 231, 231);
  }
</style>

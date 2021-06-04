<script lang="ts">
  import router from "page";

  // Include our Routes
  import Home from "./routes/Home.svelte";
  import Menu from "./routes/Menu.svelte";
  import AddTemplate from "./routes/AddTemplate.svelte"; 

  let page;
  let params;

  // Set up the pages to watch for
  router("/", () => (page = Home));
  router(
    "/menu/:privateKey",

    // Before we set the component
    (ctx, next) => {
      params = ctx.params;
      next();
    },

    // Finally set the component
    () => (page = Menu)
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


  // Set up the router to start and actively watch for changes
  router.start();
</script>

<svelte:component this={page} {params} />

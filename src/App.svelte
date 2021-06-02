<script lang="ts">
  import router from "page";

  // Include our Routes
  import Home from "./routes/Home.svelte";
  import Product from "./routes/Product.svelte";

  let page;
  let params;

  // Set up the pages to watch for
  router("/", () => (page = Home));
  router(
    "/product/:id",

    // Before we set the component
    (ctx, next) => {
      params = ctx.params;
      next();
    },

    // Finally set the component
    () => (page = Product)
  );

  // Set up the router to start and actively watch for changes
  router.start();
</script>

<svelte:component this={page} {params} />

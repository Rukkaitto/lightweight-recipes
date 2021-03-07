<script>
  import Router from "svelte-spa-router";
  import Home from "./Home.svelte";
  import RecipePage from "./RecipePage.svelte";

  const routes = {
    "/": Home,
    "/recipe/:id": RecipePage,
  };
</script>

<svelte:head>
  <title>Lightweight Recipes Site</title>
</svelte:head>

<main>
  <Router {routes} />
</main>

<style>
</style>

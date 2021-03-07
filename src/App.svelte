<script>
  import Router from "svelte-spa-router";
  import Home from "./Home.svelte";

  const API_URL = "https://api.spoonacular.com/recipes/complexSearch";
  const API_KEY = "6c144d0905ab4f17a33e32b01c86d9ea";

  const routes = {
    "/": Home,
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

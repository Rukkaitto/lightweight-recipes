<script>
  import { onMount } from "svelte";

  const APP_ID = "f6a74723";
  const API_URL = "https://api.edamam.com/search";
  const API_KEY = "0bf969053b1ed8fa981b4e4fd8e85534";

  export let params = {};

  let uri = encodeURIComponent("http://www.edamam.com/ontologies/edamam.owl#recipe_" + params.id);
  let recipe = {};

  onMount(async () => {
    fetch(`${API_URL}?app_id=${APP_ID}&app_key=${API_KEY}&r=${uri}`)
      .then((response) => response.json())
      .then((response) => {
        recipe = response[0];
      });
  });

</script>

<div id="recipe">
  <h1>{recipe.label}</h1>
  <ul>
    {#if recipe.ingredientLines}
      {#each recipe.ingredientLines as ingredient}
      <li>
        {ingredient}
      </li>
      {/each}
    {/if}
   
  </ul>
</div>

<style>
  ul {
    padding-left: 20px;
  }
</style>
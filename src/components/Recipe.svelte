<script>
  export let image = "";
  export let label = "";
  export let totalTime = "";
  export let ingredientLines = [];
  export let uri = "";

  $: id = uri.split("_")[1];
</script>

<div id="recipe">
  <img src={image} />
  <div id="text">
    <h2>
      {label}
    </h2>
    {#if totalTime}
      <h3>
        {totalTime} minutes
      </h3>
    {/if}
    <h4>Ingredients:</h4>
    <ul>
      {#each ingredientLines as ingredient}
        <li>
          {ingredient}
        </li>
      {/each}
    </ul>
    <a href={`#/recipe/${id}`}>See recipe</a>
  </div>
</div>

<style>
  #recipe {
    display: flex;
    flex-direction: row;
    background-color: #d6daf0;
    margin: 20px;
  }
  img {
    margin: 20px;
  }
  #text {
    display: flex;
    flex-direction: column;
    margin: 20px;
  }
  ul {
    padding-left: 20px;
  }
</style>

<script>
  import Recipe from "./components/Recipe.svelte";

  const APP_ID = "f6a74723";
  const API_URL = "https://api.edamam.com/search";
  const API_KEY = "0bf969053b1ed8fa981b4e4fd8e85534";

  let searchText = "";
  let searchResults = [];

  function handleClick() {
    search();
  }

  function submit(event) {
    if (event.key == "Enter") {
      search();
    }
  }

  function search() {
    fetch(`${API_URL}?app_id=${APP_ID}&app_key=${API_KEY}&q=${searchText}`)
      .then((response) => response.json())
      .then((response) => {
        searchResults = response.hits;
      });
  }
</script>

<main>
  <input
    bind:value={searchText}
    type="text"
    placeholder="Search recipes..."
    on:keydown={submit}
  />
  <button on:click={handleClick}>Search</button>

  {#each searchResults as searchResult}
    <Recipe {...searchResult.recipe} />
  {/each}
</main>

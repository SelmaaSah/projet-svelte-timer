<script>
  import { eggs } from "../../data/eggs.js";
  import EggRecipe from "./EggRecipe.svelte";

  export let onSelect;
</script>

<h2>Eggs</h2>

{#each eggs as egg}
  <EggRecipe {egg} {onSelect}/>
{/each}
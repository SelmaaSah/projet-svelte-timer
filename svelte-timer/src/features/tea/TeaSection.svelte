<script>
  import { teas } from "../../data/teas.js";
  import TeaCard from "./TeaCard.svelte";

  export let onSelect;
</script>

<h2>Tea</h2>

{#each teas as tea}
  <TeaCard {tea} {onSelect}/>
{/each}
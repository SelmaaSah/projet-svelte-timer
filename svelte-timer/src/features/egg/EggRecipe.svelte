<script>
  export let egg;
  export let onSelect;
</script>

<div class="recipe-card">
  <h2>{egg.name}</h2>
  
  {#if egg.image}
    <img src={egg.image} alt={egg.name} class="recipe-image" />
  {/if}

  <p>Temps réel : <code>{egg.time}s</code></p>

  <div class="recipe-steps">
    <h3>Recette :</h3>
    <ol>
      {#each egg.recipe as step}
        <li>{step}</li>
      {/each}
    </ol>
  </div>

  <button class="counter" on:click={() => onSelect(egg.time / 20)}>
    Démarrer le timer 
  </button>
</div>
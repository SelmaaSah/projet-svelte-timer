<script>
  export let tea;
  export let onSelect;
</script>

<div class="recipe-card">
  <h2>{tea.name}</h2>
  
  {#if tea.image}
    <img src={tea.image} alt={tea.name} class="recipe-image" />
  {/if}

  <p>🌡️ <code>{tea.temperature}°C</code> | ⏱️ <code>{tea.time}s</code></p>
  <p class="recipe-desc">{tea.description}</p>

  <button class="counter" on:click={() => onSelect(tea.time / 20)}>
    Démarrer le timer
  </button>
</div>
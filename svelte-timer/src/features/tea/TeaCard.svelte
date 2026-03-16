<script>
  export let tea;
  export let onSelect;
</script>

<div class="card">
  <h3>{tea.name}</h3>
  <p>{tea.temperature}°C</p>
  <p>{tea.time}s</p>

  <button on:click={() => onSelect(tea.time)}>
    Start timer
  </button>
</div>
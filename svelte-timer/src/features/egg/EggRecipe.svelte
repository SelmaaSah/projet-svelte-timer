<script>
  export let egg;
  export let onSelect;
</script>

<div class="card">
  <h3>{egg.name}</h3>
  <p>{egg.time}s</p>

  <button on:click={() => onSelect(egg.time)}>
    Start timer
  </button>
</div>
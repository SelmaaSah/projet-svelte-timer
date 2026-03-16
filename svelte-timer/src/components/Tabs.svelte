<script>
  export let active = "tea";
  export let onChange;
</script>

<div class="tabs">
  <button on:click={() => onChange("tea")}>Tea</button>
  <button on:click={() => onChange("egg")}>Eggs</button>
</div>

<style>
.tabs{
  display:flex;
  gap:10px;
  justify-content:center;
}
</style>
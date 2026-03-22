<script>
  export let progress = 0;
  export let color = "var(--accent)";
</script>

<div class="bar">
  <div class="fill" style="width: {progress}%; background-color: {color};"></div>
</div>

<style>
.bar {
  width: 100%;
  height: 12px;
  background: var(--border); /* Utilisation de ta variable CSS globale */
  border-radius: 6px;
  overflow: hidden;
}

.fill {
  height: 100%;
  /* C'est cette ligne qui crée l'animation fluide de la barre ! */
  transition: width 1s linear, background-color 0.3s ease;
}
</style>
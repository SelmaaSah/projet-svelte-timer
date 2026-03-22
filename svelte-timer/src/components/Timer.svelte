<script>
  import { onDestroy } from "svelte";
  import { formatTime } from "../lib/timer.js";
  import ProgressBar from "./ProgressBar.svelte";

  export let duration = 0;

  let remaining = duration;
  let interval;
  
  // État pour contrôler l'affichage de la notification
  let showNotif = false; 

  function start(){
    clearInterval(interval);
    showNotif = false; // On cache la notif au (re)démarrage

    interval = setInterval(()=>{
      if(remaining > 0){
        remaining--;
      } else {
        clearInterval(interval);
      }
    }, 1000);
  }

  function reset(){
    clearInterval(interval);
    remaining = duration;
    showNotif = false;
  }

  onDestroy(() => {
    clearInterval(interval);
  });

  $: progress = duration ? ((duration - remaining) / duration) * 100 : 0;
  
  $: if(duration){
    reset();
    start();
  }
  
  $: color = remaining <= 10 ? "red" : "var(--accent)";

  // tentative d'ajouter un son audio lorsqu'il ne reste que 10 sec mais non supporté par le navigateur 
  //$: if (remaining === 10) {
    //const audio = new Audio('src/assets/bip.mp3');

    //audio.play().catch(e => console.warn("Son bloqué par le navigateur", e));

    //showNotif = true;
  //}

</script>

<div class="timer">
  <h2>{formatTime(remaining)}</h2>

  <ProgressBar {progress} {color}/>
  
  <div class="notif-zone">
    {#if showNotif}
      <p class="notif-text">⚠️ Plus que 10 secondes !</p>
    {/if}
  </div>
  
  <button class="counter" on:click={start}>Démarrer</button>
  <button class="counter" on:click={reset}>Redémarrer</button>
</div>

<style>
  .notif-zone {
    height: 30px; /* Réserve l'espace pour éviter que les boutons sautent quand le texte apparaît */
    margin: 10px 0;
  }

  .notif-text {
    color: red;
    font-weight: bold;
    margin: 0;
    /* Petite animation CSS pour attirer l'oeil */
    animation: pulse 1s infinite alternate;
  }

  @keyframes pulse {
    from { opacity: 1; transform: scale(1); }
    to { opacity: 0.7; transform: scale(1.05); }
  }
</style>
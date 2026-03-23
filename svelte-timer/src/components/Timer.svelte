<script>
  import { onDestroy } from "svelte";
  import { formatTime } from "../lib/timer.js";
  import ProgressBar from "./ProgressBar.svelte";

  export let duration = 0;

  let remaining = 0;
  let interval;
  let showNotif = false;
  let isRunning = false; // pour savoir si le timer est en cours

  // Si duration change, on réinitialise
  $: if (!isRunning && duration) {
    remaining = duration;
    showNotif = false;
  }

  function start(){
    if (isRunning) return; // évite de lancer plusieurs intervalles
    isRunning = true;
    showNotif = false;
    
    interval = setInterval(()=>{
      if(remaining > 0){
        remaining--;
        if(remaining <= 10) showNotif = true;
      } else {
        clearInterval(interval);
        isRunning = false;
        playSound();
      }
    }, 1000);
  }

  function reset(){
    clearInterval(interval);
    remaining = duration;
    showNotif = false;
    isRunning = false;
  }

  onDestroy(() => {
    clearInterval(interval);
  });

  $: progress = duration ? ((duration - remaining) / duration) * 100 : 0;
  $: color = remaining <= 10 ? "red" : "var(--accent)";

  function playSound(){
    const audio = new Audio("/bell.mp3");
    audio.play();
  }
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
    height: 30px; 
  }

  .notif-text {
    color: red;
    font-weight: bold;
    margin: 0;
    animation: pulse 1s infinite alternate;
  }

  @keyframes pulse {
    from { opacity: 1; transform: scale(1); }
    to { opacity: 0.7; transform: scale(1.05); }
  }
</style>
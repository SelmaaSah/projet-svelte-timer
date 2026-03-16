<script>
  import { formatTime } from "../lib/timer.js";
  import ProgressBar from "./ProgressBar.svelte";

  export let duration = 0;

  let remaining = duration;
  let interval;

  function start(){
    clearInterval(interval);

    interval = setInterval(()=>{
      if(remaining > 0){
        remaining--;
      } else {
        clearInterval(interval);
      }
    },1000);
  }

  function reset(){
    clearInterval(interval);
    remaining = duration;
  }


  $: progress = duration ? ((duration - remaining) / duration) * 100 : 0;
  $: if(duration){
  reset();
  start();
}
$: color = remaining < 10 ? "var(--accent-color)" : "var(--green-color)";
</script>

<div class="timer">
  <h2>{formatTime(remaining)}</h2>

  <ProgressBar {progress} {color}/>
  <button on:click={start}>Start</button>
  <button on:click={reset}>Reset</button>
</div>
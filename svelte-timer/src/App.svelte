<script>
  import Header from "./components/Header.svelte";
  import Tabs from "./components/Tabs.svelte";
  import Timer from "./components/Timer.svelte";

  import TeaSection from "./features/tea/TeaSection.svelte";
  import EggSection from "./features/egg/EggSection.svelte";

  let tab = "tea";
  let timerDuration = 0;

  function changeTab(t){
    tab = t;
  }

  function startTimer(time){
  timerDuration = time;
}
</script>

<Header/>

<Tabs active={tab} onChange={changeTab}/>

{#if tab === "tea"}
  <TeaSection onSelect={startTimer}/>
{:else}
  <EggSection onSelect={startTimer}/>
{/if}

{#if timerDuration}
  <Timer duration={timerDuration}/>
{/if}
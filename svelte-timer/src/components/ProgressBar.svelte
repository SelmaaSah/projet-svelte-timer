<script>
  export let progress = 0;
  export let color = "var(--green-color)";
</script>

<div class="bar">
 <div class="fill" style="width:{progress}%; background:{color}"></div>
</div>

<style>
.bar{
  width:100%;
  height:10px;
  background:#eee;
}

.fill{
  height:100%;
}
</style>
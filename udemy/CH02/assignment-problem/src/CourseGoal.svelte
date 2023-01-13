<script>
  export let doHighlight
  $: doHighlight = goal.includes("!")
</script>

<h1 class:highlight={doHighlight}>{goal}</h1>

<style>
  .highlight {
    color: red;
  }
</style>

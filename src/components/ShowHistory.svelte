<script>
  export let items = [];
</script>

<div class="outer">
  {#each items as item, i}
    <li>Step: {i + 1}</li>
    <div class="inner">
      <li>Ops: {item.operation}</li>
      <li>Result: {item.result}</li>
    </div>
  {/each}
</div>

<script>
  export let operation, result;
</script>

<div class="showtext">
  {operation}
  {#if result != null}
    {result}
  {/if}
</div>

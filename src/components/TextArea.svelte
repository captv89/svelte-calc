<script>
  export let operation, result;
</script>

<div class="showtext">
  {#if result != null}
    {operation} <br />
    <p class="result">{result}</p>
  {:else}
    {operation}
  {/if}
</div>

<style>
  .showtext {
    position: relative;
    margin-bottom: 10px;
    font-size: 2em;
    text-align: right;
    text-indent: 20px;
    background-color: black;
    color: white;
    padding: 10px;
    border-radius: 10px;
    border: 1px solid white;
    height: 30vh;
    width: 95%;
  }
  .result {
    position: absolute;
    border-top: 1px solid white;
    top: 50%;
    right: 4px;
    font-size: 1.5em;
  }
</style>

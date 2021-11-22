<script>
  export let props, myClass;
</script>

<button on:click class={myClass}>
  {props}
</button>

<style>
  button {
    color: black;
    width: 50px;
    height: 50px;
    padding: 3px;
    margin: 3px;
    border-radius: 30%;
  }
  .numbers {
    background-color: rgb(255, 153, 0);
    color: white;
  }
  .operators {
    background-color: rgb(255, 94, 0);
    color: white;
  }
  .equal {
    background-color: rgb(75, 179, 6);
    color: white;
  }
  .clear {
    background-color: rgb(255, 0, 0);
    color: white;
  }
  .history {
    background-color: rgb(0, 0, 0);
    color: white;
    width: 80%;
    border-radius: 10px;
  }
</style>

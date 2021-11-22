<script>
  import MainFrame from "./components/MainFrame.svelte";
  import TextArea from "./components/TextArea.svelte";
  import CustomButton from "./components/CustomButton.svelte";
  import ShowHistory from "./components/ShowHistory.svelte";
  import { history } from "./store.js";

  let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0];
  let operators = ["+", "-", "*", "/"];
  let mathOps = "";
  let result = undefined;
  let showPastHistory = false;
  const clearAll = () => {
    mathOps = "";
    result = undefined;
    console.log("Clear All Clicked", mathOps);
  };
  const showResult = () => {
    result = eval(mathOps);
    addToHistory(mathOps, result);
    console.log("Show Result Clicked", result, $history);
  };
  const keepWriting = (value) => {
    mathOps += value;
    console.log("Keep Writing Clicked", value);
  };
  const clearLast = () => {
    mathOps = mathOps.slice(0, -1);
    console.log("Clear Last Clicked", mathOps);
  };
  const toggleHistory = () => {
    showPastHistory = !showPastHistory;
    console.log("Toggle History Clicked", showPastHistory);
  };
  const addToHistory = (mathOps, result) => {
    $history = [
      ...$history,
      {
        operation: mathOps,
        result: result,
      },
    ];
    console.log("History", history);
  };
  const clearHistory = () => {
    history.length = 0;
    console.log("History", history);
  };
  const clearLastHistory = () => {
    history.pop();
    console.log("History", history);
  };
</script>

<main>
  <MainFrame>
    {#if result !== undefined}
      <TextArea operation={mathOps} {result} />
    {:else}
      <TextArea operation={mathOps} result="" />
    {/if}
    <!-- Div for Numbers -->
    <div class="numbers">
      {#each numbers as number}
        <CustomButton
          on:click={() => keepWriting(number)}
          props={number}
          myClass="numbers"
        />
      {/each}
    </div>
    <!-- Div for Operators -->
    <div class="operators">
      {#each operators as operator}
        <CustomButton
          on:click={() => keepWriting(operator)}
          props={operator}
          myClass="operators"
        />
      {/each}

      <!-- Clear operation -->
      <CustomButton on:click={clearAll} props="AC" myClass="clear" />
      <!-- Backspace -->
      <CustomButton on:click={clearLast} props="C" myClass="clear" />
      <!-- Equals -->
      <CustomButton on:click={showResult} props="=" myClass="equal" />
      <!-- Show History -->
      <CustomButton
        on:click={toggleHistory}
        props="History"
        myClass="history"
      />
    </div>
  </MainFrame>
  {#if showPastHistory}
    <ShowHistory items={$history} />
  {/if}
</main>

<style>
  main {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    width: 100vw;
    margin: 0 0;
    background-color: bisque;
  }
  .numbers {
    justify-content: space-evenly;
    align-items: center;
    float: left;
    width: 65%;
  }
  .operators {
    justify-content: space-evenly;
    align-items: center;
    float: right;
    width: 35%;
  }
</style>

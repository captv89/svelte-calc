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
    <TextArea operation={mathOps} result="" />
    {#if result !== undefined}
      <TextArea operation="" {result} />
    {/if}
    <!-- Div for Numbers -->
    <div class="numbers">
      {#each numbers as number}
        <CustomButton on:click={() => keepWriting(number)} props={number} />
      {/each}
    </div>
    <!-- Div for Operators -->
    <div class="operators">
      {#each operators as operator}
        <CustomButton on:click={() => keepWriting(operator)} props={operator} />
      {/each}
    </div>
    <!-- Clear operation -->
    <CustomButton on:click={clearAll} props="AC" />
    <!-- Backspace -->
    <CustomButton on:click={clearLast} props="C" />
    <!-- Equals -->
    <CustomButton on:click={showResult} props="=" />
    <!-- Show History -->
    <CustomButton on:click={toggleHistory} props="History" />
  </MainFrame>
  {#if showPastHistory}
    <ShowHistory items={$history} />
  {/if}
</main>

<script>

  function getRandomInt(max) {
      return Math.floor(Math.random() * max);
  }

  let target;

  let north = "";
  let west = "";
  let east = "";
  let south = "";

  function startNewRound() {
    thumbs = "";
    north = "";
    west = "";
    east = "";
    south = "";

    const seed = getRandomInt(8);
    const value1 = seed;
    const value2 = seed + 1;
    const value3 = seed + 2;
    const value4 = seed + 3;
    console.log(value1);
    target = value1 + value2 + value3 + value4;
  }

  function checkAnswers() {
    console.log("Check answers", north, target, east);
    
    if ((target - 6) / 4 == parseInt(north)) {
      // user is correct
      thumbs = "up";
      setTimeout(startNewRound, 1000);
    } else {
      // user is NOT correct
      thumbs = "down";
    }

  }
  let thumbs = "";

  startNewRound();
</script>

<main>
  <div id="plus-container">
    <button id="button" on:click={checkAnswers}>Check</button>
    <input tabindex="1" bind:value={north} id="north" class="box" type="number">
    <div id="thumbs">{ thumbs }</div>

    <input tabindex="4" bind:value={west} id="west" class="box" type="number">
    <div id="target">{ target }</div>
    <input tabindex="2" bind:value={east} id="east" class="box" type="number">

    <input tabindex="3" bind:value={south} id="south" class="box" type="number">
  </div>
</main>

<style>
  #plus-container {
      display: grid;
      grid-template-columns: auto auto auto;
      justify-content: center;
      align-content: center;
      justify-items: center;
      align-items: center;
      font-size: 32px;
  }

  #south {
      grid-row: 3;
      grid-column: 2;
  }

  .box {
      height: 100px;
      width: 100px;
      /* border: 2px solid black; */
      text-align: center;
      font-size: 2rem;
  }
</style>


<script lang="ts">
  let word = "bøsse";

  let arr = word.split("");

  let arr2 = [];

  let message = "";

  let x = "";

  let bogstav = "";

  let ord = "";

  let hula = "";

  let lives = 7;

  let game = 1;

  arr.forEach((lol) => {
    arr2.push("x");
  });

  arr2.forEach((lol) => {
    x = x + lol;
  });

  function checkBogstav() {
    hula = hula + bogstav + ",";
    if (!arr.includes(bogstav)) {
      message = "Wrong guess";
      lives = lives - 1;
      checkLives();
      return;
    }

    let index = arr.indexOf(bogstav);
    x = "";

    arr2[index] = bogstav;

    arr2.forEach((lol) => {
      x = x + lol;
    });

    message = "";
  }

  function checkOrd() {
    if (ord != word) {
      message = "Wrong guess";
      lives = lives - 1;
      checkLives();
      return;
    }
    message = "You guessed correct!!!!";
    x = word;
  }

  function checkLives() {
    if (lives <= 0) {
      message = "You are dead";
      game = 0;
    }
  }
</script>

<h1>{x}</h1>
<p>Guessed letters: {hula}</p>
<p>Remaining lives: {lives}</p>
<p>{message}</p>

{#if game != 0}
  <label>Bogstav</label>
  <input type="text" bind:value={bogstav} />
  <button on:click={checkBogstav}>Submit bogstav</button>
  <br />
  <label>Ord</label>
  <input type="text" bind:value={ord} />
  <button on:click={checkOrd}>Submit ord</button>
{/if}

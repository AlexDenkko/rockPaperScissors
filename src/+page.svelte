<script>
  import rockImg from "./lib/assets/rock.png";
  import paperImg from "./lib/assets/paper.png";
  import scissorsImg from "./lib/assets/scissors.png";
  import githubImg from "./lib/assets/github.png";

  let userScore = 0;
  let cmpScore = 0;
  let kukavoitti = "Onnea peliin!";

  function getComputerChoise() {
    const choises = ["r", "s", "p"];
    const randomNumber = Math.floor(Math.random() * 3);
    return choises[randomNumber];
  }

  function win() {
    userScore++;
    kukavoitti = "Sinä voitit! ✅";
  }

  function lose() {
    cmpScore++;
    kukavoitti = "Sinä hävisit! ❌";
  }

  function draww() {
    kukavoitti = "Tasapeli! 🤝";
  }

  function game(userChoice) {
    const ComputerChoise = getComputerChoise();
    switch (userChoice + ComputerChoise) {
      case "rs":
      case "pr":
      case "sp":
        win();
        break;
      case "sr":
      case "rp":
      case "ps":
        lose();
        break;
      case "rr":
      case "pp":
      case "ss":
        draww();
        break;
    }
  }

  function onClickRock(event) {
    game("r");
  }

  function onClickScissors(event) {
    game("s");
  }

  function onClickPaper(event) {
    game("p");
  }
</script>

<header>
  <h1>Kivi Sakset Paperi</h1>
  <a href="https://github.com/AlexDenkko" target="_blank"
    ><img id="github" src={githubImg} alt="github" /></a
  >
</header>

<div id="fullgame">
  <div class="score-board">
    <p id="userScoreTag">Käyttäjä {userScore}</p>
    <p id="cmpScoreTag">Tietokone {cmpScore}</p>
  </div>

  <div class="result">
    <p>{kukavoitti}</p>
  </div>

  <div class="choise">
    <button id="rockClick" on:click={onClickRock}>
      <img id="rock" class="zoom" src={rockImg} alt="rockimage" />
    </button>

    <button id="scissorsClick" on:click={onClickScissors}>
      <img id="scissors" src={scissorsImg} alt="scissorsimage" />
    </button>

    <button id="paperClick" on:click={onClickPaper}>
      <img id="paper" src={paperImg} alt="paperimage" />
    </button>
  </div>
  <p id="action-messenge">Valitse kolmesta vaihtoehdosta!</p>
</div>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  :global(body) {
    background: #313235;
  }

  header {
    background: white;
    display: flex;
    flex-direction: column-reverse;
    align-items: center;
    padding-bottom: 20px;
    padding-top: 5px;
  }

  header h1 {
    color: #313235;
    text-align: center;
    font-family: sans-serif;
  }

  #fullgame {
    color: white;
    font-family: sans-serif;
  }

  .score-board {
    border-style: solid;
    border-color: white;
    border-width: 5px;
    width: 235px;
    margin: 30px auto;
    font-size: 30px;
    border-radius: 8px;
    padding: 20px;
    background-color: #313235;
    border-radius: 8px;
    padding: 20px;
    background-color: #313235;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }

  .result {
    font-size: 40px;
    text-align: center;
  }

  .choise {
    margin: 50px;
    display: flex;
    flex-direction: row;
    justify-content: center;
  }

  #rock {
    border-style: solid;
    border-color: white;
    border-width: 2px;
    border-radius: 50%;
    width: 200px;
    height: auto;
    margin: 0px 20px;
    transition: transform 0.2s;
  }
  #rock:hover {
    cursor: pointer;
    border-color: rgb(247, 95, 234);
    transform: scale(1.1);
  }

  #paper {
    border-style: solid;
    border-color: white;
    border-width: 2px;
    border-radius: 50%;
    width: 200px;
    height: auto;
    margin: 0px 20px;
    transition: transform 0.2s;
  }
  #paper:hover {
    cursor: pointer;
    border-color: cyan;
    transform: scale(1.1);
  }

  #scissors {
    border-style: solid;
    border-color: white;
    border-width: 2px;
    border-radius: 50%;
    width: 200px;
    height: auto;
    margin: 0px 20px;
    transition: transform 0.2s;
  }
  #scissors:hover {
    cursor: pointer;
    border-color: yellow;
    transform: scale(1.1);
  }

  #action-messenge {
    text-align: center;
    font-size: 25px;
  }

  .choise button {
    background: transparent;
    border: none !important;
    font-size: 0;
  }

  #github {
    width: 80px;
    margin: 0;
    transition: transform 0.2s;
    border-radius: 50%;
  }
  #github:hover {
    transform: scale(1.1);
  }
</style>

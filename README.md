# GuessTheLyrics.github.io
<!DOCTYPE html>
<a href="jeu.html">Jouer</a>

<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <title>Devine les paroles</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background-color: #f5f5f5;
      padding: 20px;
    }

    h1 {
      margin-bottom: 30px;
    }

    .song-list button {
      display: block;
      margin: 10px auto;
      padding: 12px 25px;
      font-size: 18px;
      cursor: pointer;
      border-radius: 10px;
      border: none;
      background-color: #4CAF50;
      color: white;
    }

    .song-list button:hover {
      background-color: #45a049;
    }

    .lyrics {
      font-size: 22px;
      margin: 20px;
      line-height: 1.8;
    }

    .hidden {
      background-color: black;
      color: black;
      padding: 2px 6px;
      border-radius: 4px;
      margin: 2px;
      display: inline-block;
    }

    .revealed {
      color: green;
      font-weight: bold;
      margin: 2px;
    }

    input {
      padding: 10px;
      font-size: 16px;
      width: 200px;
    }

    .back-btn {
      margin-top: 20px;
      padding: 8px 20px;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <h1> Devine les paroles </h1>

  <!-- Page d'accueil -->
  <div id="home">
    <h2>Choisis une chanson</h2>
    <div class="song-list" id="songList"></div>
  </div>

  <!-- Page du jeu -->
  <div id="game" style="display:none">
    <div class="lyrics" id="lyrics"></div>

    <input type="text" id="guessInput" placeholder="Tape un mot..." />
    <button onclick="checkWord()">Valider</button>

    <br>
    <button class="back-btn" onclick="goHome()">⬅ Retour accueil</button>
  </div>

  <script>
    const songs = [
      {
        title: "Song1",
        lyrics: "Hey Bungalow Bill What did you kill Bungalow Bill Hey Bungalow Bill What did you kill Bungalow Bill He went out tiger hunting with his elephant and gun In case of accidents he always took his mum Hes the all American bulletheaded Saxon mothers son All the children sing Hey Bungalow Bill What did you kill Bungalow Bill Hey Bungalow Bill What did you kill Bungalow Bill Deep in the jungle where the mighty tiger lies Bill and his elephants were taken by surprise So Captain Marvel zapped him right between the eyes All the children sing Hey Bungalow Bill What did you kill Bungalow Bill Hey Bungalow Bill What did you kill Bungalow Bill The children asked him if to kill was not a sin Not when he looked so fierce his mummy butted in If looks could kill it would have been us instead of him All the children sing Hey Bungalow Bill What did you
"
      },
      {
        title: "Song2",
        lyrics: "Picture yourself in a boat on a river With tangerine trees and marmalade skies Somebody calls you you answer quite slowly A girl with kaleidoscope eyes Cellophane flowers of yellow and green Towering over your head Look for the girl with the sun in her eyes And she's gone Lucy in the sky with diamond Lucy in the sky with diamonds Lucy in the sky with diamonds ahh Follow her down to a bridge by a fountain Where rocking horse people eat marshmallow pies Everyone smiles as you drift past the flowers That grow so incredibly high Newspaper taxis appear on the shore Waiting to take you away Climb in the back with your head in the clouds And you're gone Lucy in the sky with diamonds Lucy in the sky with diamonds Lucy in the sky with diamonds ahh Picture yourself on a train in a station With plasticine porters with looking glass ties Suddenly someone is there at the turnstile The girl with kaleidoscope eyes Lucy in the sky with diamonds Lucy in the sky with diamonds Lucy in the sky with diamonds ahh Lucy in the sky with diamonds Lucy in the sky with diamonds Lucy in the sky with diamonds ahh Lucy in the sky with diamonds Lucy in the sky with diamonds Lucy in the sky-"
      }
    ];

    let words = [];
    const guessedWords = new Set();

    const lyricsDiv = document.getElementById("lyrics");
    const homeDiv = document.getElementById("home");
    const gameDiv = document.getElementById("game");

    function createSongButtons() {
      const list = document.getElementById("songList");
      list.innerHTML = "";

      songs.forEach((song, index) => {
        const btn = document.createElement("button");
        btn.textContent = song.title;
        btn.onclick = () => startGame(index);
        list.appendChild(btn);
      });
    }

    function startGame(index) {
      guessedWords.clear();
      words = songs[index].lyrics.split(/\s+/);

      homeDiv.style.display = "none";
      gameDiv.style.display = "block";

      displayLyrics();
    }

    function goHome() {
      gameDiv.style.display = "none";
      homeDiv.style.display = "block";
      document.getElementById("guessInput").value = "";
    }

    function displayLyrics() {
      lyricsDiv.innerHTML = "";

      words.forEach(word => {
        const span = document.createElement("span");

        if (guessedWords.has(word.toLowerCase())) {
          span.textContent = word;
          span.className = "revealed";
        } else {
          span.textContent = "████";
          span.className = "hidden";
        }

        lyricsDiv.appendChild(span);
        lyricsDiv.appendChild(document.createTextNode(" "));
      });
    }

    function checkWord() {
      const input = document.getElementById("guessInput");
      const guess = input.value.trim().toLowerCase();

      if (guess === "") return;

      guessedWords.add(guess);
      input.value = "";

      displayLyrics();

      const allGuessed = words.every(word => guessedWords.has(word.toLowerCase()));

      if (allGuessed) {
        setTimeout(() => alert("Bravo ! Tu as trouvé toutes les paroles 🎉"), 100);
      }
    }

    createSongButtons();
  </script>

</body>
</html>

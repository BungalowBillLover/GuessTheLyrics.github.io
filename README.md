

<!DOCTYPE html>
<html lang="fr">

  
  <head>
  <meta charset="UTF-8">
   <link rel="icon" type="image/jpg" href="cat_paul_mccartney.jpg">
  <title>Devine les paroles</title>
 
  
  <style>
  
    
  body {
      font-family: "Comic Sans MS", Comic Sans, sans-serif;
    text-align: center;
      background-color: rgb(255,215,0);
      padding: 0;
      margin: 0;
  }
      .banner img {
  width: 100%;
  height: auto;
  display: block;
}

    p {
  background-image: url('beatles_banner.png');
  background-repeat: repeat;
}
      
    }

    h1 { margin-bottom: 30px; }

    .song-list button {
  font-size: 18px;
  background-color: #008542;
  color: #fff;
  text-shadow: 0 2px 0 rgb(0 0 0 / 25%);
  display: inline-flex;
  align-items: center;
  justify-content: center;
  position: relative;
  border: 0;
  z-index: 1;
  user-select: none;
  cursor: pointer;
  text-transform: uppercase;
  letter-spacing: 1px;
  white-space: unset;
  padding: 0.8rem 1.5rem;
  text-decoration: none;
  font-weight: 900;
  transition: all 0.7s cubic-bezier(0, 0.8, 0.26, 0.99);
}

button:before {
  position: absolute;
  pointer-events: none;
  top: 0;
  left: 0;
  display: block;
  width: 100%;
  height: 100%;
  content: "";
  transition: 0.7s cubic-bezier(0, 0.8, 0.26, 0.99);
  z-index: -1;
  background-color: #008542 !important;
  box-shadow: 0 -4px rgb(21 108 0 / 50%) inset,
    0 4px rgb(100 253 31 / 99%) inset, -4px 0 rgb(100 253 31 / 50%) inset,
    4px 0 rgb(21 108 0 / 50%) inset;
}

button:after {
  position: absolute;
  pointer-events: none;
  top: 0;
  left: 0;
  display: block;
  width: 100%;
  height: 100%;
  content: "";
  box-shadow: 0 4px 0 0 rgb(0 0 0 / 15%);
  transition: 0.7s cubic-bezier(0, 0.8, 0.26, 0.99);
}

button:hover:before {
  box-shadow: 0 -4px rgb(0 0 0 / 50%) inset, 0 4px rgb(255 255 255 / 20%) inset,
    -4px 0 rgb(255 255 255 / 20%) inset, 4px 0 rgb(0 0 0 / 50%) inset;
}

button:hover:after {
  box-shadow: 0 4px 0 0 rgb(0 0 0 / 15%);
}

button:active {
  transform: translateY(4px);
}

button:active:after {
  box-shadow: 0 0px 0 0 rgb(0 0 0 / 15%);

    }

    .song-list button:hover { background-color: #45a049; }

    .lyrics { font-size: 11px; margin: 20px; line-height: 1.8; }
    .hidden { background-color: black; color: black; padding: 2px 6px; border-radius: 4px; margin: 2px; display: inline-block; }
    .revealed { color: green; font-weight: bold; margin: 2px; }
    input { padding: 10px; font-size: 16px; width: 200px; }
    .back-btn { margin-top: 20px; padding: 8px 20px; cursor: pointer; }

  
  </style>
</head>





<body>

  <div class="banner">
  <img src="beatles_banner.png" alt="Bannière du site">
</div>
  
  <img src="cat_paul_mccartney.jpg" alt="cat_paul_mccartney.jpg" width="200" height="245">
  <h1>Devine les paroles</h1>

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
    <button class="back-btn" onclick="goHome()"> Retour accueil</button>
    let words = songs[index].lyrics.split(/<br\s*\/?>|\s+/i);
  </div>

  <script>
    const songs = [
      {
        title: "Song1",
        lyrics: "Hey Bungalow Bill What did you kill Bungalow Bill <BR> Hey Bungalow Bill What did you kill Bungalow Bill <BR> He went out tiger hunting with his elephant and gun <BR> In case of accidents he always took his mum <BR> Hes the all American bulletheaded Saxon mothers son <BR> All the children sing <BR> Hey Bungalow Bill What did you kill Bungalow Bill <BR> Hey Bungalow Bill What did you kill Bungalow Bill <BR> Deep in the jungle where the mighty tiger lies <BR> Bill and his elephants were taken by surprise <BR> So Captain Marvel zapped him right between the eyes <BR> All the children sing <BR> Hey Bungalow Bill What did you kill Bungalow Bill <BR> Hey Bungalow Bill What did you kill Bungalow Bill <BR> The children asked him if to kill was not a sin <BR> Not when he looked so fierce his mummy butted in <BR> If looks could kill it would have been us instead of him <BR> All the children sing <BR> Hey Bungalow Bill What did you"
      },
      {
        title: "Song2",
        lyrics: "Picture yourself in a boat on a river With tangerine trees and marmalade skies Somebody calls you you answer quite slowly A girl with kaleidoscope eyes Cellophane flowers of yellow and green Towering over your head Look for the girl with the sun in her eyes And she's gone Lucy in the sky with diamond Lucy in the sky with diamonds Lucy in the sky with diamonds ahh Follow her down to a bridge by a fountain Where rocking horse people eat marshmallow pies Everyone smiles as you drift past the flowers That grow so incredibly high Newspaper taxis appear on the shore Waiting to take you away Climb in the back with your head in the clouds And you're gone Lucy in the sky with diamonds Lucy in the sky with diamonds Lucy in the sky with diamonds ahh Picture yourself on a train in a station With plasticine porters with looking glass ties Suddenly someone is there at the turnstile The girl with kaleidoscope eyes Lucy in the sky with diamonds Lucy in the sky with diamonds Lucy in the sky with diamonds ahh Lucy in the sky with diamonds Lucy in the sky with diamonds Lucy in the sky with diamonds ahh Lucy in the sky with diamonds Lucy in the sky with diamonds Lucy in the sky"

      }, 
      {
        title: "Song3",
        lyrics: "I look at all the lonely people I look at all the lonely people Eleanor Rigby picks up the rice In the church where a wedding has been Lives in a dream Waits at the window wearing the face That she keeps in a jar by the door Who is it for All the lonely people Where do they all come from All the lonely people Where do they all belong Father McKenzie writing the words Of a sermon that no one will hear No one comes near Look at him working, darning his socks In the night when there's nobody there What does he care All the lonely people Where do they all come from All the lonely people Where do they all belong Ah look at all the lonely people Ah look at all the lonely people Eleanor Rigby died in the church And was buried along with her name Nobody came Father McKenzie wiping the dirt From his hands as he walks from the grave No one was saved All the lonely people Where do they all come from All the lonely people Where do they all belong"
      },
        {
          title: "Song4", 
          lyrics: "Yesterday All my troubles seemed so far away Now it looks as though they're here to stay Oh I believe in yesterday Suddenly I'm not half the man I used to be There's a shadow  hanging over me Oh yesterday came suddenly Why she had to go I don't know she wouldn't say I said something wrong now I long for yesterday Yesterday Love was such an easy game to play Now I need a place to hide away Oh I believe in yesterday Why she had to go I don't know she wouldn't say I said something wrong, now I long for yesterday Yesterday Love was such an easy game to play Now I need a place to hide away Oh I believe in yesterday"
      }, 
      {
        title: "Song5", 
        lyrics: "When I find myself in times of trouble Mother Mary comes to me Speaking words of wisdom let it be And in my hour of darkness she is standing right in front of me Speaking words of wisdom let it be Let it be let it be let it be let it be Whisper words of wisdom let it be And when the broken hearted people living in the world agree There will be an answer let it be For though they may be parted there is still a chance that they will see There will be an answer let it be Let it be let it be let it be let it be There will be an answer let it be Let it be let it be let it be let it be Whisper words of wisdom let it be Let it be let it be let it be let it be Whisper words of wisdom let it be be And when the night is cloudy there is still a light that shines on me Shining until tomorrow let it be I wake up to the sound of music Mother Mary comes to meSpeaking words of wisdom let it be And let it be let it be let it be let it be whisper words of wisdom let it be And let it be let it be let it be let it be Whisper words of wisdom let it be"
      }, 
      
      {
        title: "Song6", 
        lyrics: "In the town where I was born Lived a man who sailed to sea And he told us of his life In the land of submarines So we sailed on to the sun Til we found a sea of green And we lived beneath the waves In our yellow submarine We all live in a yellow submarine Yellow submarine yellow submarine We all live in a yellow submarine Yellow submarine yellow submarine And our friends are all aboard Many more of them live next door And the band begins to play We all live in a yellow submarine Yellow submarine yellow submarine We all live in a yellow submarine Yellow submarine yellow submarine As we live a life of ease a life of ease Everyone of us Has all we need Sky of blue And sea of green In our yellow Submarine We all live in a yellow submarine A yellow submarine yellow submarine We all live in a yellow submarine A yellow submarine yellow submarine We all live in a yellow submarine Yellow submarine yellow submarine We all live in a yellow submarine Yellow submarine yellow submarine"
      },
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
      if (!guess) return;
      guessedWords.add(guess);
      input.value = "";
      displayLyrics();
      if (words.every(word => guessedWords.has(word.toLowerCase()))) {
        setTimeout(() => alert("Bravo ! Tu as trouvé toutes les paroles 🎉"), 100);
      }
    }

    createSongButtons();
  </script>

</body>
</html>

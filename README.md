# AnishifyMusicPlayer


// The HTML Code is

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Anishify</title>
    <link rel="stylesheet" href="Anishify.css" />
  </head>
  <body>
    <!-- Code for the navigation bar -->
    <nav>
      <ul>
        <li class="brand">
          <img src="Anishify/Anishifylogo.jpeg" alt="Anishify" />Anishify
        </li>
        <li>Home</li>
        <li>Library</li>
        <li>Playlist</li>
      </ul>
    </nav>
    <div class="container">
      <div class="songList">
        <h1>Daily Pop Playlist</h1>
        <div class="playlist">
          <div class="songitem">

            <!-- We need not mention scr for img here as we have already set the image using the array defined in the javascript  -->

            <img alt="1" srcset="" />
            <span class="songName">Spaceship - AP Dhillon</span>
            <span class="songlistplay"
              ><span class="timestamp"
                >3:51 <i id="1" class=" songitemPlay fa-solid fa-circle-play"></i></span
            ></span>
          </div>
          <div class="songitem">
            <img alt="1" srcset="" />
            <span class="songName">Last One Standing - Eminen</span>
            <!-- <img src="Anishify/Playing.gif" alt="" srcset="" /> -->
            <span class="songlistplay"
              ><span class="timestamp"
                >6:11 <i id="2"  class="songitemPlay fa-solid fa-circle-play"></i></span
            ></span>
          </div>
          </div>
          <div class="songitem">
            <img  alt="1" srcset="" />
            <span class="songName">Lean On - Major </span>
            <!-- <img src="Anishify/Playing.gif" alt="" srcset="" /> -->
            <span class="songlistplay"
              ><span class="timestamp"
                >6:11 <i id="3"  class="songitemPlay  fa-solid fa-circle-play"></i></span
            ></span>
          </div>
          <div class="songitem">
            <img alt="1" srcset="" />
            <span class="songName">Animals - Morron 5</span>
            <!-- <img src="Anishify/Playing.gif" alt="" srcset="" /> -->
            <span class="songlistplay"
              ><span class="timestamp"
                >3:51 <i  id="4" class="songitemPlay  fa-solid fa-circle-play"></i></span
            ></span>
          </div>
        </div>
      </div>

      <div class="songBanner"></div>
    </div>
    <!-- Code for the bottom music player  -->
    <div class="bottom">
      <input
        type="range"
        name="range"
        id="myProgressbar"
        min="0"
        value="0"
        max="100"
      />
      <div class="icons">
        <!-- Addition of font awesome icons -->
        <i id = "previous" class="fa-solid fa-3x fa-backward-fast"></i>
        <i class="fa-solid fa-3x fa-backward"></i>
        <i class="fa-solid fa-3x fa-circle-play" id="masterPlay"></i>
        <i class="fa-solid fa-3x fa-forward"></i>
        <i id = "next" class="fa-solid fa-3x fa-forward-fast"></i>
      </div>
      <div class="songinfo">
        <img src="Anishify/Playing.gif" alt="" srcset="" id="gif" />
      </div>
    </div>

    <script src="Anishify.js"></script>
    <script
      src="https://kit.fontawesome.com/1f195ac66e.js"
      crossorigin="anonymous"
    ></script>
  </body>
</html>


-----------------------------------------------------------------------------------------------------------------------
The css code is 

@import url("https://fonts.googleapis.com/css2?family=Noto+Serif:ital@1&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Noto+Serif:ital,wght@1,700&display=swap");
/* CSS RESET */
* {
  margin: 0;
  padding: 0;
}

body {
  background-color: antiquewhite;
}

/* Designing of the navbar */
nav {
  background-color: black;
}
nav ul {
  display: flex;
  color: white;
  /* padding: 0px 12px; */
}

nav ul li {
  padding: 0px 12px;
  list-style: none;
  font-family: "Noto Serif", serif;
}

.brand img {
  height: 50px;
  width: 60px;
  border-radius: 30px;
  padding: 0px 15px;
}

.brand {
  display: flex;
  padding: 0px 15px;
  font-family: "Noto Serif", serif;
}

/* Designing of the bottom */
.bottom {
  position: sticky;
  background-color: white;
  height: 130px;
  bottom: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
/* To place the player bar at the bottom  */
.container {
  min-height: 75vh;
  background-color: black;
  margin: 23px auto;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  width: 70%;
  color: white;
  background-image: url("Anishify/Container.webp");
  /* background-size: 300px 100px; */
  background-repeat: no-repeat;
}
#myProgressbar {
  width: 60vh;
}

.icons {
  margin-top: 12px;
}
.icons i {
  cursor: pointer;
  padding: 5px 12px;
}

/* Designing of the songs in the song list  */
.songitem img {
  height: 50px;
  width: 60px;
}

.songitem {
  height: 50px;
  width: 60%;
  background-color: antiquewhite;
  color: black;
  display: flex;
  margin: 12px 5px;
  justify-content: space-between;
  align-items: center;
  border-radius: 30px;
}
.songinfo {
  position: absolute;
  left: 200px;
  margin-top: 25px;
}
.songinfo img {
  height: 41px;
  width: 51px;
  opacity: 1;
  transition: opacity 0.4s ease-in-out;
}
/* WHen the song will be played the palying.gif will work  */
#gif {
  opacity: 0;
}
------------------------------------------------------------------------------------------------------
The javascript logic is 


// Javascript file for Anishify.com

console.log("Welcome to Anishify.com - The Best Music player ");
// Initializing the variables
let songIndex = 0;
let audioElement = new Audio("Anishify/song/1.mp3");
let masterPlay = document.getElementById("masterPlay");
let myProgressbar = document.getElementById("myProgressbar");
let gif = document.getElementById("gif");
let songitem = Array.from(document.getElementsByClassName("songitem"));
// Creating an array with key value pair
let songs = [
  {
    songName: "Spaceship",
    filepath: "song/1.mp3",
    coverPath: "Anishify/covers/spaceshipcover.jpg",
  },
  {
    songName: "Lastone Standing",
    filepath: "song/2.mp3",
    coverPath: "Anishify/covers/lastonelogo.jpg",
  },
  {
    songName: "LeanOn - Major Lazer ",
    filepath: "song/3.mp3",
    coverPath: "Anishify/covers/Leanon.jpg",
  },
  {
    songName: "Animals - Mooron 5",
    filepath: "song/4.mp3",
    coverPath: "Anishify/covers/Animals.jpg",
  },
];

// Setting up the songnames using the array in the javascript

// ***IMP Code
// ------------------------------
songitem.forEach((element, i) => {
  console.log(element, i);
  element.getElementsByTagName("img")[0].src = songs[i].coverPath;
  element.getElementsByClassName("songName")[0].innerText = songs[i].songName;
});

// ------------------------------

let i = 0;
// Handle play pause click
masterPlay.addEventListener("click", () => {
  if ((audioElement.pause && i == 0) || audioElement.currentTime <= 0) {
    audioElement.play();
    i = 1;
    // To change the view of the play button
    masterPlay.classList.remove("fa-circle-play");
    masterPlay.classList.add("fa-circle-pause");
    gif.style.opacity = 1;
  } else {
    audioElement.pause();
    i = 0;
    // To change the view of the play button
    masterPlay.classList.remove("fa-circle-pause");
    masterPlay.classList.add("fa-circle-play");
    gif.style.opacity = 0;
  }
});

// For updating the time of the audio
audioElement.addEventListener("timeupdate", () => {
  console.log("timeupdate");

  // To update the progressbar
  progress = parseInt((audioElement.currentTime / audioElement.duration) * 100);
  // console.log(progress);

  // Parse Int  function is used to convert the given input into integer value
  myProgressbar.value = progress;
});

// Creating a function to seek the song as per conveince
myProgressbar.addEventListener("change", () => {
  audioElement.currentTime =
    (myProgressbar.value * audioElement.duration) / 100;
});

// Defining a function so that when we click on one music's play buttuon the play from other fets removed

const Makeallplays = () => {
  Array.from(document.getElementsByClassName("songitemPlay")).forEach(
    (element) => {
      element.classList.remove("fa-circle-pause");
      element.classList.add("fa-circle-play");
    }
  );
};

// To define a function so that when a song is played using the playlist it plays
Array.from(document.getElementsByClassName("songitemPlay")).forEach(
  (element) => {
    element.addEventListener("click", (e) => {
      Makeallplays();
      songIndex = parseInt(e.target.id);
      e.target.classList.remove("fa-circle-play");
      e.target.classList.add("fa-circle-pause");
      audioElement.src = `Anishify/song/${songIndex}.mp3`;
      audioElement.currentTime = 0;
      audioElement.play();
      masterPlay.classList.remove("fa-circle-play");
      masterPlay.classList.add("fa-circle-pause");
    });
  }
);

// ADdingg the function for the previous button
document.getElementById("next").addEventListener("click", () => {
  if (songIndex >= 4) {
    songIndex = 0;
  } else {
    songIndex += 1;
  }

  // e.target.classList.remove("fa-circle-play");
  // e.target.classList.add("fa-circle-pause");
  audioElement.src = `Anishify/song/${songIndex}.mp3`;
  audioElement.currentTime = 0;
  audioElement.play();
  masterPlay.classList.remove("fa-circle-play");
  masterPlay.classList.add("fa-circle-pause");
});

document.getElementById("previous").addEventListener("click", () => {
  if (songIndex <= 0) {
    songIndex = 4;
  } else {
    songIndex -= 1;
  }

  // e.target.classList.remove("fa-circle-play");
  // e.target.classList.add("fa-circle-pause");
  audioElement.src = `Anishify/song/${songIndex}.mp3`;
  audioElement.currentTime = 0;
  audioElement.play();
  masterPlay.classList.remove("fa-circle-play");
  masterPlay.classList.add("fa-circle-pause");
});
--------------------------------------------------

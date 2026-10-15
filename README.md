
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Aditya Smart TV</title>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Arial, sans-serif;
}

body {
  background: #080b16;
  color: white;
  min-height: 100vh;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 25px 6%;
  background: #101629;
}

.logo {
  font-size: 26px;
  font-weight: bold;
  color: #49b8ff;
}

header span {
  color: #ccc;
}

.hero {
  padding: 65px 7%;
  background:
    linear-gradient(90deg, #080b16 10%, #080b16aa),
    url("https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?auto=format&fit=crop&w=1600&q=80")
    center/cover;
}

.hero h1 {
  font-size: clamp(35px, 6vw, 65px);
  margin-bottom: 18px;
}

.hero p {
  color: #ddd;
  max-width: 500px;
  line-height: 1.7;
  margin-bottom: 25px;
}

button {
  background: #168bff;
  color: white;
  border: none;
  padding: 13px 22px;
  border-radius: 7px;
  cursor: pointer;
  font-size: 15px;
}

button:hover {
  background: #0066cc;
}

section.apps {
  padding: 35px 6%;
}

h2 {
  margin-bottom: 22px;
}

.app-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(135px, 1fr));
  gap: 18px;
}

.app {
  background: #171e32;
  border: 2px solid transparent;
  border-radius: 12px;
  min-height: 125px;
  padding: 22px 10px;
  text-align: center;
  cursor: pointer;
  transition: .2s;
}

.app:hover, .app:focus {
  transform: translateY(-5px);
  border-color: #49b8ff;
  outline: none;
}

.app .icon {
  font-size: 37px;
  margin-bottom: 12px;
}

.app p {
  font-weight: bold;
}

.player {
  display: none;
  margin: 10px 6% 35px;
  padding: 25px;
  background: #151d31;
  border-radius: 12px;
}

.player.active {
  display: block;
}

.player p {
  color: #ccc;
  margin: 15px 0;
  line-height: 1.6;
}

footer {
  padding: 25px;
  text-align: center;
  color: #999;
  background: #101629;
}

@media (max-width: 500px) {
  header {
    gap: 12px;
    flex-wrap: wrap;
  }
  .hero {
    padding-top: 50px;
    padding-bottom: 50px;
  }
}
</style>
</head>

<body>

<header>
  <div class="logo">📺 ADITYA TV</div>
  <span id="clock">Smart Entertainment</span>
</header>

<div class="hero">
  <h1>Your Smart TV.<br>Unlimited Fun.</h1>
  <p>
    Welcome to Aditya Singh's Smart TV website.
    Explore entertainment apps, music, videos and more
    from one beautiful dashboard.
  </p>
  <button onclick="openApp('Featured Entertainment')">
    Explore Now ▶
  </button>
</div>

<section class="apps">
  <h2>My Apps</h2>
  <div class="app-grid">

    <div class="app" tabindex="0"
         onclick="openApp('YouTube')">
      <div class="icon">▶️</div>
      <p>YouTube</p>
    </div>

    <div class="app" tabindex="0"
         onclick="openApp('Netflix')">
      <div class="icon">🎬</div>
      <p>Netflix</p>
    </div>

    <div class="app" tabindex="0"
         onclick="openApp('Music')">
      <div class="icon">🎵</div>
      <p>Music</p>
    </div>

    <div class="app" tabindex="0"
         onclick="openApp('Web Browser')">
      <div class="icon">🌐</div>
      <p>Browser</p>
    </div>

    <div class="app" tabindex="0"
         onclick="openApp('Games')">
      <div class="icon">🎮</div>
      <p>Games</p>
    </div>

    <div class="app" tabindex="0"
         onclick="openApp('Settings')">
      <div class="icon">⚙️</div>
      <p>Settings</p>
    </div>

  </div>
</section>

<div class="player" id="player">
  <h2 id="appTitle">Welcome</h2>
  <p id="appDescription"></p>
  <button id="launchButton" onclick="launchApp()">
    Open App
  </button>
  <button onclick="closeApp()" style="background:#414b60">
    Back
  </button>
</div>

<footer>
  © 2026 Aditya Singh | Smart TV Interface
</footer>

<script>
const appLinks = {
  "YouTube": "https://www.youtube.com/",
  "Netflix": "https://www.netflix.com/",
  "Music": "https://music.youtube.com/",
  "Web Browser": "https://www.google.com/",
  "Games": "https://www.crazygames.com/",
  "Settings": ""
};

let selectedApp = "";

function openApp(name) {
  selectedApp = name;

  document.getElementById("appTitle").textContent = name;
  document.getElementById("appDescription").textContent =
    name === "Settings"
      ? "This demo TV interface is ready to customize."
      : "Select Open App to visit " + name +
        ". Availability depends on your device and browser.";

  document.getElementById("launchButton").style.display =
    appLinks[name] ? "inline-block" : "none";

  document.getElementById("player").classList.add("active");
  document.getElementById("player").scrollIntoView({
    behavior: "smooth",
    block: "center"
  });
}

function launchApp() {
  const url = appLinks[selectedApp];
  if (url) {
    window.open(url, "_blank", "noopener,noreferrer");
  }
}

function closeApp() {
  document.getElementById("player").classList.remove("active");
}

function updateClock() {
  document.getElementById("clock").textContent =
    new Date().toLocaleTimeString([], {
      hour: "2-digit",
      minute: "2-digit"
    });
}

updateClock();
setInterval(updateClock, 1000);
</script>

</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Midnight Garden</title>

<style>
body {
  margin: 0;
  overflow: hidden;
  background: radial-gradient(circle at center, #140000, #000000 70%);
  font-family: serif;
  cursor: crosshair;
}

h1 {
  position: fixed;
  width: 100%;
  text-align: center;
  top: 30px;
  color: #ffb3c6;
  letter-spacing: 4px;
  font-size: 34px;
  text-shadow: 0 0 12px #ff2e63, 0 0 30px #ff2e63;
}

.sub {
  position: fixed;
  width: 100%;
  text-align: center;
  top: 75px;
  color: #aaa;
  font-size: 14px;
  letter-spacing: 2px;
}

.flower {
  position: absolute;
  font-size: 30px;
  animation: bloom 4s ease-out forwards;
  pointer-events: none;
  filter: drop-shadow(0 0 8px #ff4d6d);
}

@keyframes bloom {
  0% { transform: scale(0.4) translateY(0); opacity: 1; }
  100% { transform: scale(1.6) translateY(-160px); opacity: 0; }
}

.petal {
  position: absolute;
  color: #ff758f;
  font-size: 18px;
  animation: fall linear forwards;
  opacity: 0.7;
}

@keyframes fall {
  to {
    transform: translateY(110vh);
    opacity: 0;
  }
}

.controls {
  position: fixed;
  bottom: 20px;
  right: 20px;
}

button {
  background: #2a0000;
  color: #ff9aa2;
  border: 1px solid #ff4d6d;
  padding: 10px 16px;
  border-radius: 25px;
  cursor: pointer;
  box-shadow: 0 0 10px #ff4d6d;
}
</style>
</head>

<body>

<h1>🌹 MIDNIGHT GARDEN 🌹</h1>
<div class="sub">click to make it bloom</div>

<!-- Background Music -->
<audio id="bgm" loop>
  <source src="bgm.mp3" type="audio/mp3">
</audio>

<!-- Bloom Sound -->
<audio id="clickSound">
  <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_c8c8a73467.mp3" type="audio/mp3">
</audio>

<div class="controls">
  <button onclick="toggleMusic()">🎵 Music</button>
</div>

<script>
const flowers = ["🌹","🥀","🌺","🌸"];
let musicStarted = false;

// click bloom
document.addEventListener("click", e => {
  bloom(e.clientX, e.clientY);
  startMusicOnce();
});

// create bloom
function bloom(x, y) {
  const f = document.createElement("div");
  f.className = "flower";
  f.innerText = flowers[Math.floor(Math.random()*flowers.length)];
  f.style.left = x + "px";
  f.style.top = y + "px";
  document.body.appendChild(f);

  const s = document.getElementById("clickSound");
  s.currentTime = 0;
  s.play();

  setTimeout(() => f.remove(), 4000);
}

// falling petals background
function createPetal() {
  const p = document.createElement("div");
  p.className = "petal";
  p.innerText = "❀";
  p.style.left = Math.random()*100 + "vw";
  p.style.animationDuration = (6 + Math.random()*6) + "s";
  document.body.appendChild(p);
  setTimeout(() => p.remove(), 12000);
}
setInterval(createPetal, 600);

// music control
function startMusicOnce() {
  if (!musicStarted) {
    document.getElementById("bgm").play();
    musicStarted = true;
  }
}

function toggleMusic() {
  const bgm = document.getElementById("bgm");
  if (bgm.paused) bgm.play();
  else bgm.pause();
}
</script>

</body>
</html># GitHub Pages

_Create a site or blog from your GitHub repositories with GitHub Pages._

## Welcome

- **Who is this for**: Beginners, students, project maintainers, small businesses.
- **What you'll learn**: How to build a GitHub Pages site.
- **What you'll build**: We'll build a simple GitHub Pages site with a blog. We'll use [Jekyll](https://jekyllrb.com), a static site generator.
- **Prerequisites**: If you need to learn about branches, commits, and pull requests, take [Introduction to GitHub](https://github.com/skills/introduction-to-github) first.

- **How long**: This exercise takes less than one hour to complete.

In this exercise, you will:

1. Enable GitHub Pages
1. Configure your site
1. Customize your home page
1. Create a blog post
1. Merge your pull request


### How to start this exercise

Simply copy the exercise to your account, then give your favorite Octocat (Mona) **about 20 seconds** to prepare the first lesson, then **refresh the page**.

[![](https://img.shields.io/badge/Copy%20Exercise-%E2%86%92-1f883d?style=for-the-badge&logo=github&labelColor=197935)](https://github.com/new?template_owner=skills&template_name=github-pages&owner=%40me&name=skills-github-pages&description=Exercise:+Create+a+site+or+blog+from+your+GitHub+repositories+with+GitHub+Pages&visibility=public)

<details>
<summary>Having trouble? 🤷</summary><br/>

When copying the exercise, we recommend the following settings:

- For owner, choose your personal account or an organization to host the repository.

- We recommend creating a public repository, since private repositories will use Actions minutes.

If the exercise isn't ready in 20 seconds, please check the [Actions](../../actions) tab.

- Check to see if a job is running. Sometimes it simply takes a bit longer.

- If the page shows a failed job, please submit an issue. Nice, you found a bug! 🐛

</details>

---

&copy; 2025 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

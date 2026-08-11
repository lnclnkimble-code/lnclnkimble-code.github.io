<!DOCTYPE html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

```
<title>Game Hub</title>

<style>
    * {
        box-sizing: border-box;
    }

    body {
        margin: 0;
        font-family: Arial, sans-serif;
        background: #111827;
        color: white;
    }

    /* TOP BAR */
    header {
        height: 70px;
        background: #1f2937;
        display: flex;
        align-items: center;
        padding: 0 30px;
        gap: 30px;
        position: sticky;
        top: 0;
        z-index: 10;
        box-shadow: 0 3px 15px rgba(0, 0, 0, 0.4);
    }

    .logo {
        font-size: 26px;
        font-weight: bold;
        white-space: nowrap;
    }

    .logo span {
        color: #60a5fa;
    }

    .search {
        flex: 1;
        max-width: 500px;
    }

    .search input {
        width: 100%;
        padding: 12px 18px;
        border-radius: 25px;
        border: none;
        outline: none;
        font-size: 15px;
        background: #374151;
        color: white;
    }

    .search input::placeholder {
        color: #9ca3af;
    }

    /* MAIN CONTENT */
    main {
        max-width: 1300px;
        margin: auto;
        padding: 35px 25px;
    }

    .welcome {
        margin-bottom: 30px;
    }

    .welcome h1 {
        margin: 0 0 8px;
        font-size: 36px;
    }

    .welcome p {
        color: #9ca3af;
        margin: 0;
    }

    /* CATEGORIES */
    .categories {
        display: flex;
        gap: 10px;
        flex-wrap: wrap;
        margin-bottom: 35px;
    }

    .category {
        border: none;
        background: #374151;
        color: white;
        padding: 10px 18px;
        border-radius: 20px;
        cursor: pointer;
        font-size: 14px;
    }

    .category:hover {
        background: #4b5563;
    }

    .category.active {
        background: #3b82f6;
    }

    /* GAME GRID */
    .section-title {
        font-size: 24px;
        margin-bottom: 18px;
    }

    .games {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(210px, 1fr));
        gap: 20px;
    }

    .game-card {
        background: #1f2937;
        border-radius: 12px;
        overflow: hidden;
        cursor: pointer;
        transition: transform 0.2s, box-shadow 0.2s;
    }

    .game-card:hover {
        transform: translateY(-5px);
        box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
    }

    .game-image {
        width: 100%;
        height: 135px;
        background: linear-gradient(135deg, #2563eb, #7c3aed);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 45px;
    }

    .game-info {
        padding: 14px;
    }

    .game-info h3 {
        margin: 0 0 5px;
        font-size: 17px;
    }

    .game-info p {
        margin: 0;
        color: #9ca3af;
        font-size: 13px;
    }

    /* GAME PLAYER */
    #gameScreen {
        display: none;
        position: fixed;
        inset: 0;
        background: #000;
        z-index: 100;
    }

    #gameFrame {
        width: 100%;
        height: 100%;
        border: none;
    }

    .gameControls {
        position: absolute;
        top: 15px;
        left: 15px;
        display: flex;
        gap: 10px;
        z-index: 101;
    }

    .gameButton {
        border: none;
        background: rgba(31, 41, 55, 0.9);
        color: white;
        padding: 10px 15px;
        border-radius: 8px;
        cursor: pointer;
        font-size: 14px;
    }

    .gameButton:hover {
        background: rgba(59, 130, 246, 0.95);
    }

    /* MOBILE */
    @media (max-width: 600px) {
        header {
            padding: 0 15px;
            gap: 15px;
        }

        .logo {
            font-size: 20px;
        }

        main {
            padding: 25px 15px;
        }

        .welcome h1 {
            font-size: 28px;
        }
    }
</style>
```

</head>

<body>

```
<header>
    <div class="logo">🎮 Game<span>Hub</span></div>

    <div class="search">
        <input
            type="text"
            id="searchBox"
            placeholder="Search games..."
            onkeyup="searchGames()">
    </div>
</header>

<main>

    <div class="welcome">
        <h1>Play Games</h1>
        <p>Pick a game and start playing.</p>
    </div>

    <div class="categories">
        <button class="category active" onclick="filterGames('all', this)">
            All
        </button>

        <button class="category" onclick="filterGames('action', this)">
            Action
        </button>

        <button class="category" onclick="filterGames('arcade', this)">
            Arcade
        </button>

        <button class="category" onclick="filterGames('puzzle', this)">
            Puzzle
        </button>

        <button class="category" onclick="filterGames('sports', this)">
            Sports
        </button>
    </div>

    <div class="section-title">
        Games
    </div>

    <div class="games" id="gameList">

        <!-- GAME 1 -->
        <div class="game-card"
             data-name="Example Game"
             data-category="arcade"
             onclick="openGame('https://example.com')">

            <div class="game-image">
                🎯
            </div>

            <div class="game-info">
                <h3>Example Game</h3>
                <p>Arcade</p>
            </div>
        </div>

        <!-- GAME 2 -->
        <div class="game-card"
             data-name="Space Game"
             data-category="action"
             onclick="openGame('https://example.com')">

            <div class="game-image">
                🚀
            </div>

            <div class="game-info">
                <h3>Space Game</h3>
                <p>Action</p>
            </div>
        </div>

        <!-- GAME 3 -->
        <div class="game-card"
             data-name="Puzzle Game"
             data-category="puzzle"
             onclick="openGame('https://example.com')">

            <div class="game-image">
                🧩
            </div>

            <div class="game-info">
                <h3>Puzzle Game</h3>
                <p>Puzzle</p>
            </div>
        </div>

        <!-- GAME 4 -->
        <div class="game-card"
             data-name="Sports Game"
             data-category="sports"
             onclick="openGame('https://example.com')">

            <div class="game-image">
                🏀
            </div>

            <div class="game-info">
                <h3>Sports Game</h3>
                <p>Sports</p>
            </div>
        </div>

    </div>

</main>

<!-- FULLSCREEN GAME PLAYER -->

<div id="gameScreen">

    <div class="gameControls">
        <button class="gameButton" onclick="closeGame()">
            ← Back
        </button>

        <button class="gameButton" onclick="fullscreenGame()">
            ⛶ Fullscreen
        </button>
    </div>

    <iframe
        id="gameFrame"
        src=""
        allowfullscreen>
    </iframe>

</div>

<script>

    function openGame(url) {
        document.getElementById("gameFrame").src = url;
        document.getElementById("gameScreen").style.display = "block";
    }

    function closeGame() {
        document.getElementById("gameFrame").src = "";
        document.getElementById("gameScreen").style.display = "none";
    }

    function fullscreenGame() {
        const frame = document.getElementById("gameFrame");

        if (frame.requestFullscreen) {
            frame.requestFullscreen();
        }
    }

    function searchGames() {

        const search =
            document.getElementById("searchBox")
            .value
            .toLowerCase();

        const games =
            document.querySelectorAll(".game-card");

        games.forEach(function(game) {

            const name =
                game.dataset.name.toLowerCase();

            if (name.includes(search)) {
                game.style.display = "block";
            } else {
                game.style.display = "none";
            }

        });
    }

    function filterGames(category, button) {

        document
            .querySelectorAll(".category")
            .forEach(function(btn) {
                btn.classList.remove("active");
            });

        button.classList.add("active");

        const games =
            document.querySelectorAll(".game-card");

        games.forEach(function(game) {

            if (
                category === "all" ||
                game.dataset.category === category
            ) {
                game.style.display = "block";
            } else {
                game.style.display = "none";
            }

        });
    }

</script>
```

</body>
</html>

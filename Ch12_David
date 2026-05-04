<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>🌱 Plant Reproduction Simulator | Fixed Bud Game</title>
    <style>
        * {
            box-sizing: border-box;
            user-select: none;
        }

        body {
            font-family: 'Segoe UI', 'Poppins', system-ui, sans-serif;
            background: #c8e6c0;  /* LIGHT GREEN background */
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            margin: 0;
        }

        .sim-card {
            max-width: 950px;
            width: 100%;
            background: #fffef7;
            border-radius: 48px;
            box-shadow: 0 25px 45px rgba(0,0,0,0.2);
            overflow: hidden;
            border: 2px solid #ffd966;
        }

        .header {
            background: #2e7d32;
            padding: 16px 20px;
            text-align: center;
            color: #fff8e7;
        }

        .header h1 {
            margin: 0;
            font-size: 1.6rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
        }

        .content {
            padding: 24px;
        }

        .concept-panel {
            background: #e8f5e9;
            border-left: 6px solid #2e7d32;
            padding: 14px 18px;
            border-radius: 20px;
            margin-bottom: 20px;
            font-size: 0.95rem;
        }

        .game-area {
            background: #f5f0e0;
            border-radius: 32px;
            padding: 25px;
            margin: 20px 0;
            min-height: 320px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            box-shadow: inset 0 0 0 2px white, 0 5px 15px rgba(0,0,0,0.1);
        }

        .btn-group {
            display: flex;
            gap: 15px;
            justify-content: center;
            flex-wrap: wrap;
            margin-top: 20px;
        }

        button {
            background: #ffb74d;
            border: none;
            padding: 12px 28px;
            font-weight: bold;
            font-size: 1rem;
            border-radius: 40px;
            cursor: pointer;
            transition: 0.08s linear;
            box-shadow: 0 3px 0 #b85e1a;
            font-family: inherit;
        }

        button:active {
            transform: translateY(2px);
            box-shadow: 0 1px 0 #b85e1a;
        }

        button:disabled {
            opacity: 0.5;
            transform: none;
            cursor: not-allowed;
        }

        .primary-btn {
            background: #2e7d32;
            color: white;
            box-shadow: 0 3px 0 #1b5e20;
        }

        /* Card flip styles for matching game */
        .match-grid {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 16px;
            margin: 20px 0;
        }

        .match-card {
            width: 90px;
            height: 90px;
            background: #ffd97c;
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.8rem;
            cursor: pointer;
            transition: 0.1s;
            box-shadow: 0 4px 0 #b07628;
        }

        .match-card.matched {
            background: #81c784;
            box-shadow: 0 2px 0 #4caf50;
            cursor: default;
            opacity: 0.7;
        }

        .match-card.selected {
            background: #ffb74d;
            transform: scale(0.96);
        }

        /* Maze styles */
        .maze {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 4px;
            background: #6b8c42;
            padding: 10px;
            border-radius: 20px;
            width: 100%;
            max-width: 400px;
            margin: 0 auto;
        }

        .maze-cell {
            aspect-ratio: 1;
            background: #c8e6a5;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
            cursor: pointer;
        }

        .wall {
            background: #5d3a1a;
            cursor: not-allowed;
        }

        .player {
            background: #ffb74d;
        }

        .goal {
            background: #ffd54f;
        }

        /* Bee catcher */
        .bee-zone {
            background: #d4e6b0;
            border-radius: 40px;
            padding: 20px;
            min-height: 160px;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 15px;
            align-items: center;
        }

        .bee-item {
            background: #ffcc80;
            padding: 12px 20px;
            border-radius: 50px;
            font-size: 1.2rem;
            font-weight: bold;
            cursor: pointer;
            transition: 0.05s;
            animation: buzz 0.4s ease infinite alternate;
        }

        @keyframes buzz {
            from { transform: translateX(0px); }
            to { transform: translateX(5px); }
        }

        /* Sequence slots */
        .seq-slot {
            background: #faecbf;
            margin: 12px auto;
            padding: 14px;
            border-radius: 60px;
            width: 95%;
            cursor: pointer;
            font-weight: bold;
            text-align: center;
            transition: 0.1s;
        }

        .seq-slot.correct {
            background: #a5d6a7;
        }

        /* Progress & feedback */
        .feedback {
            background: #fff3e0;
            padding: 12px;
            border-radius: 24px;
            margin-top: 15px;
            font-weight: 500;
            text-align: center;
        }

        .progress {
            font-weight: bold;
            margin: 12px 0;
            color: #2e7d32;
        }

        /* FIXED WHACK-A-BUD STYLES - each button shows image + word clearly */
        .whack-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            justify-items: center;
            align-items: center;
            margin: 20px 0;
            width: 100%;
            max-width: 400px;
        }
        
        .whack-cell {
            width: 100px;
            height: 100px;
            background: #8b6946;
            border-radius: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 8px;
            cursor: pointer;
            transition: 0.05s;
            box-shadow: 0 5px 0 #5a3a1a;
            font-weight: bold;
        }
        
        .whack-cell:active {
            transform: translateY(2px);
            box-shadow: 0 2px 0 #5a3a1a;
        }
        
        .whack-emoji {
            font-size: 2.5rem;
        }
        
        .whack-text {
            font-size: 0.85rem;
            background: rgba(0,0,0,0.6);
            padding: 3px 10px;
            border-radius: 20px;
            color: white;
            letter-spacing: 1px;
        }
        
        /* Hole state */
        .whack-cell.hole {
            background: #8b6946;
        }
        
        /* Bud state - bright & inviting */
        .whack-cell.bud {
            background: #ffb74d;
            animation: pulse 0.4s ease;
            box-shadow: 0 5px 0 #e67e22;
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
    </style>
</head>
<body>
<div class="sim-card" id="app"></div>

<script>
    // ----- GAME STATE -----
    let currentScene = "start";
    let gameData = { reproductionType: null, pollinationType: null };

    // ----- SCENE DEFINITIONS -----
    const scenes = {
        start: {
            title: "🌱 Choose Your Reproduction Strategy",
            concept: "Plants reproduce either asexually (mitosis → clones) or sexually (meiosis → gametes). Which path will you take?",
            renderGame: () => `<div style="font-size: 4rem;">🌿 🌸</div>`,
            setup: () => {},
            buttons: [
                { text: "🌿 Asexual (Clones via Mitosis)", action: () => { gameData.reproductionType = "asexual"; goTo("asexualHub"); } },
                { text: "🌸 Sexual (Gametes via Meiosis)", action: () => { gameData.reproductionType = "sexual"; goTo("sexualChoice"); } }
            ]
        },

        // ========== ASEXUAL HUB ==========
        asexualHub: {
            title: "🌿 Asexual Reproduction",
            concept: "Asexual reproduction uses mitotic cell division. Offspring are genetically identical clones. No fusion of gametes.",
            renderGame: () => `<div style="font-size: 3rem;">🧬 MITOSIS → CLONES 🧬</div><p style="margin-top: 12px;">Choose a learning activity:</p>`,
            setup: () => {},
            buttons: [
                { text: "🧭 Maze: Spread the Runner", action: () => goTo("asexualMaze") },
                { text: "🔨 Whack-a-Bud (Budding)", action: () => goTo("asexualWhack") },
                { text: "⏱️ Fragmentation Timing", action: () => goTo("asexualTiming") }
            ]
        },

        // MAZE GAME
        asexualMaze: {
            title: "🧭 Guide the Runner Clone to New Soil",
            concept: "Runners (stolons) are asexual clones. Spreading reduces competition with the parent plant.",
            renderGame: () => `<div id="mazeContainer" class="maze"></div><div id="mazeFeedback" class="feedback"></div>`,
            setup: () => {
                const maze = [
                    [1,1,1,1,1,1,1],
                    [1,0,0,0,1,0,1],
                    [1,1,1,0,1,0,1],
                    [1,0,0,0,0,0,1],
                    [1,0,1,1,1,0,1],
                    [1,0,0,0,0,0,1],
                    [1,1,1,1,1,1,1]
                ];
                let player = { x: 1, y: 1 };
                const goal = { x: 5, y: 5 };
                let active = true;

                function renderMaze() {
                    const container = document.getElementById("mazeContainer");
                    if (!container) return;
                    container.innerHTML = "";
                    for (let i = 0; i < maze.length; i++) {
                        for (let j = 0; j < maze[0].length; j++) {
                            const cell = document.createElement("div");
                            cell.className = "maze-cell";
                            if (maze[i][j] === 1) cell.classList.add("wall");
                            if (player.x === i && player.y === j) {
                                cell.classList.add("player");
                                cell.innerText = "🌿";
                            } else if (goal.x === i && goal.y === j) {
                                cell.classList.add("goal");
                                cell.innerText = "🏁";
                            } else cell.innerText = "";
                            cell.addEventListener("click", () => {
                                if (!active) return;
                                const dx = i - player.x;
                                const dy = j - player.y;
                                if (Math.abs(dx) + Math.abs(dy) === 1 && maze[i][j] === 0) {
                                    player = { x: i, y: j };
                                    renderMaze();
                                    if (player.x === goal.x && player.y === goal.y) {
                                        active = false;
                                        document.getElementById("mazeFeedback").innerHTML = "✅ Runner reached new soil! Clone established away from parent!";
                                        setTimeout(() => {
                                            goTo("asexualDispersal");
                                        }, 1500);
                                    }
                                } else if (Math.abs(dx) + Math.abs(dy) !== 1) {
                                    document.getElementById("mazeFeedback").innerHTML = "🚶 Move one step at a time!";
                                } else if (maze[i][j] === 1) {
                                    document.getElementById("mazeFeedback").innerHTML = "🧱 Wall blocks the way!";
                                }
                            });
                            container.appendChild(cell);
                        }
                    }
                }
                renderMaze();
            },
            buttons: []
        },

        // ========== FIXED WHACK-A-BUD GAME ==========
        // Each button shows 🌱 and "BUD" text together when active
        // Clicking collects it, then it returns to hole state
        // Only resets if timer expires, NOT when clicked
        asexualWhack: {
            title: "🔨 Whack-a-Bud: Budding Clones",
            concept: "Budding = mitotic division. Each bud becomes a new clone. Click the 🌱 BUD before it disappears!",
            renderGame: () => `
                <div id="whackGrid" class="whack-grid"></div>
                <div id="whackProgress" class="progress">🌱 Buds collected: 0 / 6</div>
                <div id="whackFeedback" class="feedback"></div>
            `,
            setup: () => {
                let collected = 0;
                let active = true;
                let spawnInterval;
                let activeBudTimeout = null;
                let currentBudCell = null;
                
                const grid = document.getElementById("whackGrid");
                const progress = document.getElementById("whackProgress");
                const feedback = document.getElementById("whackFeedback");
                
                const cells = [];
                
                // Create 9 cells (3x3 grid)
                for (let i = 0; i < 9; i++) {
                    const cell = document.createElement("div");
                    cell.className = "whack-cell hole";
                    cell.innerHTML = `
                        <div class="whack-emoji">🕳️</div>
                        <div class="whack-text">hole</div>
                    `;
                    cell.isBud = false;
                    
                    cell.addEventListener("click", () => {
                        if (!active) return;
                        
                        // If this cell currently HAS a bud, collect it
                        if (cell.isBud) {
                            // Clear the timeout that would remove this bud
                            if (activeBudTimeout) {
                                clearTimeout(activeBudTimeout);
                                activeBudTimeout = null;
                            }
                            
                            // Mark as collected
                            collected++;
                            progress.innerText = `🌱 Buds collected: ${collected} / 6`;
                            feedback.innerHTML = "✅ You caught the bud! +1 clone!";
                            
                            // Change back to hole
                            cell.isBud = false;
                            cell.className = "whack-cell hole";
                            cell.innerHTML = `
                                <div class="whack-emoji">🕳️</div>
                                <div class="whack-text">hole</div>
                            `;
                            currentBudCell = null;
                            
                            // Check win condition
                            if (collected === 6) {
                                active = false;
                                if (spawnInterval) clearInterval(spawnInterval);
                                feedback.innerHTML = "🎉 Great! All buds became clones! Time for dispersal.";
                                setTimeout(() => goTo("asexualDispersal"), 1500);
                            }
                        } else {
                            feedback.innerHTML = "⏳ No bud here! Wait for a bud to appear in a hole!";
                        }
                    });
                    
                    grid.appendChild(cell);
                    cells.push(cell);
                }
                
                // Function to spawn a bud in a random hole
                function spawnBud() {
                    if (!active) return;
                    if (collected >= 6) return;
                    
                    // If there's already an active bud, don't spawn another (single bud at a time for clarity)
                    if (currentBudCell !== null) return;
                    
                    // Get all holes that are not currently buds
                    const availableCells = cells.filter(cell => !cell.isBud);
                    if (availableCells.length === 0) return;
                    
                    const randomIndex = Math.floor(Math.random() * availableCells.length);
                    const targetCell = availableCells[randomIndex];
                    
                    // Transform this cell into a BUD with clear emoji + text
                    targetCell.isBud = true;
                    targetCell.className = "whack-cell bud";
                    targetCell.innerHTML = `
                        <div class="whack-emoji">🌱</div>
                        <div class="whack-text">BUD</div>
                    `;
                    currentBudCell = targetCell;
                    feedback.innerHTML = "🌱 A bud appeared! Click it quickly!";
                    
                    // Set timeout to revert this bud after 1.2 seconds if not clicked
                    activeBudTimeout = setTimeout(() => {
                        if (targetCell.isBud && active) {
                            // Bud disappears without being collected
                            targetCell.isBud = false;
                            targetCell.className = "whack-cell hole";
                            targetCell.innerHTML = `
                                <div class="whack-emoji">🕳️</div>
                                <div class="whack-text">hole</div>
                            `;
                            currentBudCell = null;
                            feedback.innerHTML = "💨 The bud disappeared! Wait for the next one...";
                            activeBudTimeout = null;
                        }
                    }, 1200);
                }
                
                // Spawn a new bud every 1.5 seconds
                spawnInterval = setInterval(() => {
                    if (active && collected < 6) {
                        spawnBud();
                    }
                }, 1500);
                
                // Store cleanup reference
                window._whackCleanup = () => {
                    if (spawnInterval) clearInterval(spawnInterval);
                    if (activeBudTimeout) clearTimeout(activeBudTimeout);
                };
            },
            buttons: []
        },

        // TIMING GAME
        asexualTiming: {
            title: "⏱️ Fragmentation Timing",
            concept: "Fragmentation: each piece grows into a new clone (mitosis). Click when the slider is in the GREEN zone!",
            renderGame: () => `
                <div style="width: 100%; margin: 20px 0;">
                    <div style="position: relative; height: 55px; background: #d9c49b; border-radius: 60px; cursor: pointer;" id="timingTrack">
                        <div style="position: absolute; left: 38%; width: 24%; height: 100%; background: #6fbf4c; opacity: 0.5; border-radius: 60px; pointer-events: none;"></div>
                        <div id="timingSlider" style="position: absolute; width: 22%; height: 100%; background: #ff9f3d; border-radius: 60px; left: 0%; transition: left 0.02s linear;"></div>
                    </div>
                </div>
                <div id="timingProgress" class="progress">Successful splits: 0 / 4</div>
                <div id="timingFeedback" class="feedback"></div>
                <button id="timingResetBtn" style="margin-top: 10px;">🔄 Reset Slider</button>
            `,
            setup: () => {
                let successCount = 0;
                let active = true;
                let leftPercent = 18;
                let direction = 1;
                let animId;
                const slider = document.getElementById("timingSlider");
                const track = document.getElementById("timingTrack");
                const progress = document.getElementById("timingProgress");
                const feedback = document.getElementById("timingFeedback");

                function moveSlider() {
                    if (!active) return;
                    leftPercent += direction * 1.3;
                    if (leftPercent >= 85) { direction = -1; leftPercent = 85; }
                    if (leftPercent <= 2) { direction = 1; leftPercent = 2; }
                    slider.style.left = `${leftPercent}%`;
                    animId = requestAnimationFrame(moveSlider);
                }
                function checkHit() {
                    if (!active) return;
                    if (leftPercent >= 38 && leftPercent <= 62) {
                        successCount++;
                        progress.innerText = `Successful splits: ${successCount} / 4`;
                        feedback.innerHTML = "✅ Perfect split! New clone created (mitosis).";
                        if (successCount === 4) {
                            active = false;
                            cancelAnimationFrame(animId);
                            feedback.innerHTML = "🎉 4 clones created! Time for dispersal!";
                            setTimeout(() => goTo("asexualDispersal"), 1500);
                        } else {
                            leftPercent = Math.random() * 65 + 5;
                            slider.style.left = `${leftPercent}%`;
                        }
                    } else {
                        feedback.innerHTML = "❌ Missed the green zone! Try again.";
                    }
                }
                track.addEventListener("click", (e) => {
                    if (!active) return;
                    const rect = track.getBoundingClientRect();
                    const percent = ((e.clientX - rect.left) / rect.width) * 100;
                    if (percent >= 38 && percent <= 62) checkHit();
                    else feedback.innerHTML = "❌ Click inside the green zone!";
                });
                document.getElementById("timingResetBtn")?.addEventListener("click", () => {
                    leftPercent = 18;
                    slider.style.left = "18%";
                    feedback.innerHTML = "Slider reset. Keep trying!";
                });
                moveSlider();
            },
            buttons: []
        },

        // ASEXUAL DISPERSAL
        asexualDispersal: {
            title: "🌍 Dispersal: Spread Your Clones",
            concept: "Dispersal avoids competition for light, water, and minerals. It also allows colonization of new habitats.",
            renderGame: () => `
                <div style="display: flex; gap: 15px; justify-content: center; flex-wrap: wrap; margin: 20px 0;">
                    <div class="match-card" data-hab="field" style="width: auto; padding: 12px 24px;">🌾 Open Field</div>
                    <div class="match-card" data-hab="river" style="width: auto; padding: 12px 24px;">💧 Riverbank</div>
                    <div class="match-card" data-hab="hill" style="width: auto; padding: 12px 24px;">⛰️ Sunny Hill</div>
                </div>
                <div id="disperseFeedback" class="feedback"></div>
            `,
            setup: () => {
                let clicks = 0;
                const feedback = document.getElementById("disperseFeedback");
                const habitats = document.querySelectorAll("[data-hab]");
                habitats.forEach(hab => {
                    hab.addEventListener("click", () => {
                        if (clicks >= 3) return;
                        if (hab.style.background !== "#81c784") {
                            hab.style.background = "#81c784";
                            clicks++;
                            feedback.innerHTML = `✅ Clone colonized ${hab.innerText}! (${clicks}/3) Dispersal reduces competition.`;
                            if (clicks === 3) {
                                feedback.innerHTML += `<br>🎉 Success! Clones spread far! Species survives!`;
                                setTimeout(() => goTo("final"), 1500);
                            }
                        }
                    });
                });
            },
            buttons: []
        },

        // ========== SEXUAL PATH ==========
        sexualChoice: {
            title: "🐝 Choose Pollination Method",
            concept: "Sexual reproduction uses meiosis to create gametes. Pollination method affects genetic variation.",
            renderGame: () => `<div style="font-size: 3rem;">🌸 🌼 🌻</div>`,
            setup: () => {},
            buttons: [
                { text: "🌸 Self-Pollination (Less Variation)", action: () => { gameData.pollinationType = "self"; goTo("selfGame"); } },
                { text: "🦋 Cross-Pollination (More Variation)", action: () => { gameData.pollinationType = "cross"; goTo("crossGame"); } }
            ]
        },

        // SELF: Matching game
        selfGame: {
            title: "🌸 Self-Pollination: Match the Flowers",
            concept: "Self-pollination = same flower/plant → less genetic variation. Match identical flowers!",
            renderGame: () => `<div id="selfMatchGrid" class="match-grid"></div><div id="selfProgress" class="progress">Matched: 0 / 3</div><div id="selfFeedback" class="feedback"></div>`,
            setup: () => {
                const flowers = ["🌻", "🌷", "🌸"];
                let deck = [];
                for (let i = 0; i < flowers.length; i++) {
                    deck.push({ flower: flowers[i], pairId: i, matched: false });
                    deck.push({ flower: flowers[i], pairId: i, matched: false });
                }
                for (let i = deck.length - 1; i > 0; i--) {
                    const j = Math.floor(Math.random() * (i + 1));
                    [deck[i], deck[j]] = [deck[j], deck[i]];
                }
                let selectedIndex = null;
                let matchedCount = 0;
                let lock = false;

                function render() {
                    const grid = document.getElementById("selfMatchGrid");
                    if (!grid) return;
                    grid.innerHTML = "";
                    deck.forEach((card, idx) => {
                        const cardDiv = document.createElement("div");
                        cardDiv.className = "match-card";
                        if (card.matched) {
                            cardDiv.classList.add("matched");
                            cardDiv.innerText = card.flower;
                        } else if (selectedIndex === idx && !lock) {
                            cardDiv.classList.add("selected");
                            cardDiv.innerText = card.flower;
                        } else {
                            cardDiv.innerText = "❓";
                        }
                        cardDiv.addEventListener("click", () => {
                            if (lock || card.matched) return;
                            if (selectedIndex === null) {
                                selectedIndex = idx;
                                render();
                                document.getElementById("selfFeedback").innerHTML = "Now click a second flower to match!";
                            } else if (selectedIndex === idx) {
                                selectedIndex = null;
                                render();
                            } else {
                                const first = deck[selectedIndex];
                                const second = deck[idx];
                                if (first.pairId === second.pairId) {
                                    first.matched = true;
                                    second.matched = true;
                                    matchedCount++;
                                    document.getElementById("selfProgress").innerHTML = `Matched: ${matchedCount} / 3`;
                                    selectedIndex = null;
                                    render();
                                    if (matchedCount === 3) {
                                        document.getElementById("selfFeedback").innerHTML = "✅ All matched! Self-pollination complete! Fertilization next.";
                                        setTimeout(() => goTo("fertilizationGame"), 1500);
                                    }
                                } else {
                                    lock = true;
                                    document.getElementById("selfFeedback").innerHTML = "❌ Not a match! Try again.";
                                    const tempFirst = selectedIndex;
                                    const tempSecond = idx;
                                    const cards = document.querySelectorAll(".match-card");
                                    if (cards[tempFirst]) cards[tempFirst].innerText = deck[tempFirst].flower;
                                    if (cards[tempSecond]) cards[tempSecond].innerText = deck[tempSecond].flower;
                                    setTimeout(() => {
                                        selectedIndex = null;
                                        lock = false;
                                        render();
                                    }, 800);
                                }
                            }
                        });
                        grid.appendChild(cardDiv);
                    });
                }
                render();
            },
            buttons: []
        },

        // CROSS: Catch bees game
        crossGame: {
            title: "🦋 Cross-Pollination: Catch the Bees!",
            concept: "Cross-pollination = different plants → greater genetic variation → better adaptation!",
            renderGame: () => `<div id="crossBeeZone" class="bee-zone"></div><div id="crossProgress" class="progress">Pollen transfers: 0 / 6</div><div id="crossFeedback" class="feedback"></div>`,
            setup: () => {
                let caught = 0;
                let active = true;
                let interval;
                const zone = document.getElementById("crossBeeZone");
                const progress = document.getElementById("crossProgress");
                const feedback = document.getElementById("crossFeedback");

                function spawnBee() {
                    if (!active) return;
                    const bee = document.createElement("div");
                    bee.className = "bee-item";
                    bee.innerHTML = "🐝🌸 (other plant)";
                    bee.addEventListener("click", () => {
                        if (!active) return;
                        caught++;
                        progress.innerText = `Pollen transfers: ${caught} / 6`;
                        bee.remove();
                        if (caught === 6) {
                            active = false;
                            clearInterval(interval);
                            feedback.innerHTML = "🎉 Cross-pollination success! High genetic variation!";
                            setTimeout(() => goTo("fertilizationGame"), 1500);
                        }
                    });
                    zone.appendChild(bee);
                    setTimeout(() => { if (bee.parentNode) bee.remove(); }, 1500);
                }
                interval = setInterval(() => { if (active && caught < 6) spawnBee(); }, 750);
            },
            buttons: []
        },

        // FERTILIZATION SEQUENCE
        fertilizationGame: {
            title: "🌺 Fertilization & Transformation",
            concept: "Pollen tube grows → Ovule becomes SEED, Ovary becomes FRUIT. Arrange the steps in correct order!",
            renderGame: () => `<div id="seqContainer"></div><div id="seqFeedback" class="feedback"></div><button id="seqNextBtn" disabled style="margin-top: 15px;">✨ Complete Transformation ✨</button>`,
            setup: () => {
                const correct = [
                    "🌱 Pollen lands on stigma",
                    "🌿 Pollen tube grows down style",
                    "💚 Male gamete fuses with ovule",
                    "🍎 Ovule → SEED | Ovary → FRUIT"
                ];
                let current = [...correct];
                for (let i = current.length - 1; i > 0; i--) {
                    const j = Math.floor(Math.random() * (i + 1));
                    [current[i], current[j]] = [current[j], current[i]];
                }

                function renderSeq() {
                    const container = document.getElementById("seqContainer");
                    if (!container) return;
                    container.innerHTML = "";
                    current.forEach((step, idx) => {
                        const div = document.createElement("div");
                        div.className = "seq-slot";
                        div.innerText = step;
                        div.addEventListener("click", () => {
                            if (idx < current.length - 1) {
                                [current[idx], current[idx+1]] = [current[idx+1], current[idx]];
                                renderSeq();
                                checkWin();
                            }
                        });
                        container.appendChild(div);
                    });
                }

                function checkWin() {
                    const isCorrect = JSON.stringify(current) === JSON.stringify(correct);
                    const feedback = document.getElementById("seqFeedback");
                    const nextBtn = document.getElementById("seqNextBtn");
                    if (isCorrect) {
                        feedback.innerHTML = "✅ Perfect sequence! Fertilization successful!";
                        nextBtn.disabled = false;
                        document.querySelectorAll(".seq-slot").forEach(el => el.classList.add("correct"));
                    } else {
                        feedback.innerHTML = "⚠️ Order is incorrect. Click a tile to swap with the one below it.";
                    }
                }

                renderSeq();
                document.getElementById("seqNextBtn")?.addEventListener("click", () => {
                    goTo("sexualDispersal");
                });
            },
            buttons: []
        },

        // SEXUAL DISPERSAL
        sexualDispersal: {
            title: "🍃 Seed Dispersal",
            concept: "Dispersal avoids overcrowding, reduces competition, and allows colonization of new habitats.",
            renderGame: () => `<div id="fruitZone" style="display: flex; flex-wrap: wrap; justify-content: center; gap: 15px; margin: 20px;"></div><div id="fruitProgress" class="progress">Seeds dispersed: 0 / 4</div><div id="fruitFeedback" class="feedback"></div>`,
            setup: () => {
                let collected = 0;
                let active = true;
                let interval;
                const zone = document.getElementById("fruitZone");
                const progress = document.getElementById("fruitProgress");
                const feedback = document.getElementById("fruitFeedback");

                function spawnFruit() {
                    if (!active) return;
                    const fruits = ["🍎", "🍒", "🍑", "🍓"];
                    const fruit = document.createElement("div");
                    fruit.className = "match-card";
                    fruit.style.width = "auto";
                    fruit.style.padding = "12px 24px";
                    fruit.style.fontSize = "1.8rem";
                    fruit.innerText = fruits[Math.floor(Math.random() * fruits.length)];
                    fruit.addEventListener("click", () => {
                        if (!active) return;
                        collected++;
                        progress.innerText = `Seeds dispersed: ${collected} / 4`;
                        fruit.remove();
                        if (collected === 4) {
                            active = false;
                            clearInterval(interval);
                            feedback.innerHTML = "🎉 Dispersal complete! New habitats colonized!";
                            setTimeout(() => goTo("final"), 1500);
                        }
                    });
                    zone.appendChild(fruit);
                    setTimeout(() => { if (fruit.parentNode) fruit.remove(); }, 1800);
                }
                interval = setInterval(() => { if (active && collected < 4) spawnFruit(); }, 700);
            },
            buttons: []
        },

        // FINAL
        final: {
            title: "🏆 Simulation Complete!",
            concept: gameData.reproductionType === "asexual" 
                ? "You mastered asexual reproduction: mitotic clones + dispersal = survival without competition." 
                : (gameData.pollinationType === "self" 
                    ? "Self-pollination creates less variation, but successful dispersal ensures species survival." 
                    : "Cross-pollination maximizes genetic variation! Combined with dispersal, your species is resilient and widespread."),
            renderGame: () => `<div style="font-size: 5rem;">🌍🌱🏆</div><p>You avoided overcrowding and colonized new habitats!</p>`,
            setup: () => {},
            buttons: [
                { text: "🌱 Start Over - New Plant", action: () => { gameData = { reproductionType: null, pollinationType: null }; goTo("start"); } }
            ]
        }
    };

    function goTo(sceneId) {
        // Cleanup any intervals from previous scene
        if (window._whackCleanup) {
            window._whackCleanup();
            window._whackCleanup = null;
        }
        currentScene = sceneId;
        render();
    }

    function render() {
        const scene = scenes[currentScene];
        if (!scene) return;

        const app = document.getElementById("app");
        if (!app) return;

        let buttonsHtml = "";
        if (scene.buttons && scene.buttons.length > 0) {
            buttonsHtml = `<div class="btn-group">`;
            scene.buttons.forEach(btn => {
                buttonsHtml += `<button class="primary-btn" data-btn-index="${Math.random()}">${btn.text}</button>`;
            });
            buttonsHtml += `</div>`;
        }

        app.innerHTML = `
            <div class="header">
                <h1>🔬 ${scene.title}</h1>
            </div>
            <div class="content">
                <div class="concept-panel">
                    📖 <strong>Concept Check:</strong> ${scene.concept}
                </div>
                <div class="game-area" id="gameArea">
                    ${scene.renderGame()}
                </div>
                ${buttonsHtml}
            </div>
        `;

        // Attach button listeners
        if (scene.buttons && scene.buttons.length > 0) {
            const btns = document.querySelectorAll(".primary-btn");
            btns.forEach((btn, idx) => {
                btn.addEventListener("click", scene.buttons[idx].action);
            });
        }

        // Run setup
        scene.setup();
    }

    // Start the app
    goTo("start");
</script>
</body>
</html>

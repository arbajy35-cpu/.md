# Games/carrom/carrom_mode/carrom_game/carrom.js

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `Games/carrom/carrom_mode/carrom_game/carrom.js` |
| Extension | `.js` |
| Bytes | 20937 |
| Lines | 669 |
| SHA-256 | `986695816a77e03ab87c663e25c5953bb6fd67f95eb413f77fc1c0257f1bb6dd` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`Games`

The local intelligence engine detected
0 direct dependencies
and 1 consumers.

## 5. Dependencies

- None

## 6. Used By

- `Games/carrom/carrom_mode/carrom_game/carrom.html`

## 7. Exact Relation Flow

- No local relation detected

## 8. Local Symbols

- `getCanvasPos`
- `initCoins`
- `setupPlayerNames`
- `drawBoard`
- `drawCoins`
- `drawStriker`
- `updatePhysics`
- `updateScore`
- `resetStrikerPosition`
- `switchTurn`
- `aiMove`
- `gameLoop`
- `handleStart`
- `handleMove`
- `handleEnd`
- `canvas`
- `ctx`
- `playerScoreEl`
- `aiScoreEl`
- `turnIndicator`
- `resetBtn`
- `backBtn`
- `powerFill`
- `powerValue`
- `settingsBtn`
- `urlParams`
- `GAME_MODE`
- `BOARD_SIZE`
- `POCKET_RADIUS`
- `COIN_RADIUS`
- `STRIKER_RADIUS`
- `FRICTION`
- `BASELINE_Y_PLAYER`
- `BASELINE_Y_AI`
- `BASELINE_MIN_X`
- `BASELINE_MAX_X`
- `MAX_DRAG_DISTANCE`
- `MAX_POWER`
- `coins`
- `striker`
- `isDragging`
- `isPositioning`
- `dragStart`
- `dragCurrent`
- `playerScore`
- `aiScore`
- `isPlayerTurn`
- `pocketedThisTurn`
- `gameActive`
- `hasShot`
- `aiThinking`
- `aiStatus`
- `currentPower`
- `selectedCoin`
- `foulCommitted`
- `playerNames`
- `pockets`
- `rect`
- `scaleX`
- `scaleY`
- `clientX`
- `i`
- `angle`
- `p1`
- `p2`
- `labels`
- `baselineY`
- `dx`
- `dy`
- `dragDist`
- `power`
- `shootAngle`
- `lineLength`
- `color`
- `moving`
- `nearPocket`
- `dist`
- `allObjects`
- `j`
- `a`
- `minDist`
- `overlap`
- `v1`
- `v2`
- `dir1`
- `dir2`
- `vx1`
- `vy1`
- `vx2`
- `vy2`
- `whiteLeft`
- `blackLeft`
- `winner`
- `targets`
- `bestTarget`
- `bestScore`
- `bestStrikerX`
- `bestPocket`
- `testX`
- `coinToPocket`
- `strikerToCoin`
- `angle1`
- `angle2`
- `angleDiff`
- `score`
- `angleToCoin`
- `angleCoinToPocket`
- `pos`
- `distToStriker`
- `coin`

## 9. Exports

- None

## 10. Unresolved References

- **string-path** → `/storage/emulated/0/MINIGRAM1/Games/carrom/carrom_mode/med.html`

## 11. Error / Problem Detection

- **MEDIUM** — Unresolved Local Reference: string-path: /storage/emulated/0/MINIGRAM1/Games/carrom/carrom_mode/med.html

## 12. Project Systems

- None

## 13. Project Risks

- None

## 14. Recommendations

- None

## 15. Execution / Architecture Flow

See the generated relation graph and file-level flows.

---

# ORIGINAL SOURCE CODE

The following is the **exact local source content**
read from:

`/storage/emulated/0/MINIGRAM1/Games/carrom/carrom_mode/carrom_game/carrom.js`

It is NOT AI generated or rewritten.

```javascript
const canvas = document.getElementById('carromBoard');
const ctx = canvas?.getContext('2d');
const playerScoreEl = document.getElementById('playerScore');
const aiScoreEl = document.getElementById('aiScore');
const turnIndicator = document.getElementById('turnIndicator');
const resetBtn = document.getElementById('resetBtn');
const backBtn = document.getElementById('backBtn');
const powerFill = document.getElementById('powerFill');
const powerValue = document.getElementById('powerValue');
const settingsBtn = document.getElementById('settingsBtn');

// Get game mode from URL
const urlParams = new URLSearchParams(window.location.search);
const GAME_MODE = urlParams.get('mode') || 'classic';

const BOARD_SIZE = 400;
const POCKET_RADIUS = 22;
const COIN_RADIUS = 10;
const STRIKER_RADIUS = 13;
const FRICTION = 0.985;
const BASELINE_Y_PLAYER = 320;
const BASELINE_Y_AI = 80;
const BASELINE_MIN_X = 80;
const BASELINE_MAX_X = 320;
const MAX_DRAG_DISTANCE = 100;
const MAX_POWER = 15;

let coins = [];
let striker = { x: 200, y: BASELINE_Y_PLAYER, vx: 0, vy: 0, radius: STRIKER_RADIUS };
let isDragging = false;
let isPositioning = false;
let dragStart = null;
let dragCurrent = null;
let playerScore = 0;
let aiScore = 0;
let isPlayerTurn = true;
let pocketedThisTurn = false;
let gameActive = true;
let hasShot = false;
let aiThinking = false;
let aiStatus = '';
let currentPower = 0;
let selectedCoin = null;
let foulCommitted = false;
let playerNames = ['Player 1', 'Player 2']; // 2 Player names

const pockets = [
  { x: 20, y: 20 }, { x: 380, y: 20 },
  { x: 20, y: 380 }, { x: 380, y: 380 }
];

function getCanvasPos(e) {
  const rect = canvas.getBoundingClientRect();
  const scaleX = canvas.width / rect.width;
  const scaleY = canvas.height / rect.height;

  let clientX, clientY;
  if (e.touches && e.touches.length > 0) {
    clientX = e.touches[0].clientX;
    clientY = e.touches[0].clientY;
  } else {
    clientX = e.clientX;
    clientY = e.clientY;
  }

  return {
    x: (clientX - rect.left) * scaleX,
    y: (clientY - rect.top) * scaleY
  };
}

function initCoins() {
  coins = [];
  coins.push({ x: 200, y: 200, vx: 0, vy: 0, radius: COIN_RADIUS, color: '#e63946', type: 'queen', pocketed: false });

  for (let i = 0; i < 9; i++) {
    let angle = (i / 9) * Math.PI * 2;
    coins.push({
      x: 200 + Math.cos(angle) * 22,
      y: 200 + Math.sin(angle) * 22,
      vx: 0, vy: 0,
      radius: COIN_RADIUS,
      color: '#f1faee',
      type: 'white',
      pocketed: false,
      originalX: 200 + Math.cos(angle) * 22,
      originalY: 200 + Math.sin(angle) * 22
    });
  }

  for (let i = 0; i < 9; i++) {
    let angle = (i / 9) * Math.PI * 2 + Math.PI / 9;
    coins.push({
      x: 200 + Math.cos(angle) * 44,
      y: 200 + Math.sin(angle) * 44,
      vx: 0, vy: 0,
      radius: COIN_RADIUS,
      color: '#1d3557',
      type: 'black',
      pocketed: false,
      originalX: 200 + Math.cos(angle) * 44,
      originalY: 200 + Math.sin(angle) * 44
    });
  }
}

function setupPlayerNames() {
  if (GAME_MODE === '2player') {
    const p1 = prompt('Player 1 ka naam:', 'Player 1') || 'Player 1';
    const p2 = prompt('Player 2 ka naam:', 'Mummy') || 'Player 2';
    playerNames = [p1, p2];

    // Update UI labels
    const labels = document.querySelectorAll('.player-score.label');
    if (labels[0]) labels[0].textContent = p1.toUpperCase();
    if (labels[1]) labels[1].textContent = p2.toUpperCase();

    // Update turn indicator
    if (turnIndicator) {
      turnIndicator.textContent = `${playerNames[0]}'s Turn`;
    }
  }
}

function drawBoard() {
  if (!ctx) return;

  ctx.fillStyle = '#d4a574';
  ctx.fillRect(0, 0, BOARD_SIZE, BOARD_SIZE);

  ctx.strokeStyle = '#8b4513';
  ctx.lineWidth = 3;
  ctx.strokeRect(35, 35, 330, 330);

  ctx.beginPath();
  ctx.arc(200, 200, 50, 0, Math.PI * 2);
  ctx.stroke();

  ctx.fillStyle = '#000';
  pockets.forEach(p => {
    ctx.beginPath();
    ctx.arc(p.x, p.y, POCKET_RADIUS, 0, Math.PI * 2);
    ctx.fill();
  });

  ctx.strokeStyle = isPlayerTurn? '#ff6b35' : '#e63946';
  ctx.lineWidth = 3;
  ctx.setLineDash([5, 5]);
  ctx.beginPath();
  ctx.moveTo(BASELINE_MIN_X, BASELINE_Y_PLAYER);
  ctx.lineTo(BASELINE_MAX_X, BASELINE_Y_PLAYER);
  ctx.stroke();
  ctx.beginPath();
  ctx.moveTo(BASELINE_MIN_X, BASELINE_Y_AI);
  ctx.lineTo(BASELINE_MAX_X, BASELINE_Y_AI);
  ctx.stroke();
  ctx.setLineDash([]);

  if (!hasShot && gameActive && (isPlayerTurn || GAME_MODE === '2player')) {
    ctx.fillStyle = 'rgba(69,123,157,0.25)';
    const baselineY = isPlayerTurn? BASELINE_Y_PLAYER : BASELINE_Y_AI;
    ctx.fillRect(BASELINE_MIN_X, baselineY + 15, BASELINE_MAX_X - BASELINE_MIN_X, 70);

    ctx.fillStyle = isPositioning? 'rgba(69,123,157,0.8)' : 'rgba(255,107,53,0.5)';
    ctx.beginPath();
    ctx.arc(striker.x, striker.y, striker.radius + 18, 0, Math.PI * 2);
    ctx.fill();

    ctx.fillStyle = '#fff';
    ctx.font = 'bold 11px Arial';
    ctx.textAlign = 'center';
    if (isPositioning) {
      ctx.fillText('← POSITION MODE →', striker.x, striker.y - 50);
      ctx.fillText('Release to Set', striker.x, striker.y - 35);
    } else if (GAME_MODE === 'freestyle') {
      ctx.fillText('TAP COIN to Select', striker.x, striker.y - 80);
      ctx.fillText('TAP BLUE ZONE to Position', striker.x, striker.y - 65);
      ctx.fillText('HOLD STRIKER & Pull to Shoot', striker.x, striker.y - 50);
    } else {
      ctx.fillText('TAP BLUE ZONE to Position', striker.x, striker.y - 65);
      ctx.fillText('HOLD STRIKER & Pull to Shoot', striker.x, striker.y - 50);
    }
  }

  if (aiThinking &&!isPlayerTurn && GAME_MODE!== '2player') {
    ctx.fillStyle = 'rgba(230,57,70,0.9)';
    ctx.font = 'bold 14px Arial';
    ctx.textAlign = 'center';
    ctx.fillText(aiStatus, 200, 30);
  }

  ctx.fillStyle = 'rgba(0,0,0,0.6)';
  ctx.font = 'bold 12px Arial';
  ctx.textAlign = 'left';
  ctx.fillText(GAME_MODE.toUpperCase(), 10, 20);
}

function drawCoins() {
  if (!ctx) return;

  coins.forEach(coin => {
    if (coin.pocketed) return;

    if (GAME_MODE === 'freestyle' && selectedCoin === coin) {
      ctx.beginPath();
      ctx.arc(coin.x, coin.y, coin.radius + 5, 0, Math.PI * 2);
      ctx.fillStyle = 'rgba(250,204,21,0.5)';
      ctx.fill();
    }

    ctx.beginPath();
    ctx.arc(coin.x, coin.y, coin.radius, 0, Math.PI * 2);
    ctx.fillStyle = coin.color;
    ctx.fill();
    ctx.strokeStyle = '#000';
    ctx.lineWidth = 1;
    ctx.stroke();
  });
}

function drawStriker() {
  if (!ctx) return;

  ctx.beginPath();
  ctx.arc(striker.x, striker.y, striker.radius, 0, Math.PI * 2);
  ctx.fillStyle = isPlayerTurn? '#457b9d' : '#e63946';
  ctx.fill();
  ctx.strokeStyle = '#1d3557';
  ctx.lineWidth = 2;
  ctx.stroke();

  if (isDragging &&!isPositioning && (isPlayerTurn || GAME_MODE === '2player') &&!hasShot && dragStart && dragCurrent) {
    const dx = dragCurrent.x - dragStart.x;
    const dy = dragCurrent.y - dragStart.y;
    const dragDist = Math.hypot(dx, dy);
    const power = Math.min(dragDist / MAX_DRAG_DISTANCE, 1) * MAX_POWER;
    currentPower = power;

    const shootAngle = Math.atan2(-dy, -dx);
    const lineLength = power * 5;

    let color;
    if (power < 5) color = '#4ade80';
    else if (power < 10) color = '#facc15';
    else color = '#ef4444';

    ctx.beginPath();
    ctx.moveTo(striker.x, striker.y);
    ctx.lineTo(
      striker.x + Math.cos(shootAngle) * lineLength,
      striker.y + Math.sin(shootAngle) * lineLength
    );
    ctx.strokeStyle = color;
    ctx.lineWidth = 4;
    ctx.stroke();

    ctx.beginPath();
    ctx.arc(striker.x, striker.y, striker.radius + power, 0, Math.PI * 2);
    ctx.strokeStyle = color;
    ctx.lineWidth = 2;
    ctx.stroke();
  } else {
    currentPower = 0;
  }

  if (powerFill) powerFill.style.width = (currentPower / MAX_POWER * 100) + '%';
  if (powerValue) powerValue.textContent = Math.round(currentPower);
}

function updatePhysics() {
  let moving = false;
  foulCommitted = false;

  [...coins, striker].forEach(obj => {
    if (obj.pocketed) return;

    obj.x += obj.vx;
    obj.y += obj.vy;
    obj.vx *= FRICTION;
    obj.vy *= FRICTION;

    if (Math.abs(obj.vx) > 0.1 || Math.abs(obj.vy) > 0.1) moving = true;

    let nearPocket = pockets.some(p => Math.hypot(obj.x - p.x, obj.y - p.y) < 40);

    if (!nearPocket) {
      if (obj.x - obj.radius < 20) { obj.x = 20 + obj.radius; obj.vx *= -0.8; }
      if (obj.x + obj.radius > 380) { obj.x = 380 - obj.radius; obj.vx *= -0.8; }
      if (obj.y - obj.radius < 20) { obj.y = 20 + obj.radius; obj.vy *= -0.8; }
      if (obj.y + obj.radius > 380) { obj.y = 380 - obj.radius; obj.vy *= -0.8; }
    }

    pockets.forEach(pocket => {
      let dist = Math.hypot(obj.x - pocket.x, obj.y - pocket.y);
      if (dist < POCKET_RADIUS + obj.radius * 0.8) {
        if (obj === striker) {
          if (isPlayerTurn) {
            playerScore = Math.max(0, playerScore - 1);
          } else {
            aiScore = Math.max(0, aiScore - 1);
          }
          pocketedThisTurn = false;
          foulCommitted = true;
          isPlayerTurn =!isPlayerTurn;
        } else {
          obj.pocketed = true;

          if (GAME_MODE === 'classic') {
            if (isPlayerTurn && obj.type === 'black') {
              obj.pocketed = false;
              obj.x = 200;
              obj.y = 200;
              obj.vx = 0;
              obj.vy = 0;
              playerScore = Math.max(0, playerScore - 1);
              pocketedThisTurn = false;
              foulCommitted = true;
              isPlayerTurn = false;
            } else if (!isPlayerTurn && obj.type === 'white') {
              obj.pocketed = false;
              obj.x = 200;
              obj.y = 200;
              obj.vx = 0;
              obj.vy = 0;
              aiScore = Math.max(0, aiScore - 1);
              pocketedThisTurn = false;
              foulCommitted = true;
              isPlayerTurn = true;
            } else {
              pocketedThisTurn = true;
              if (obj.type === 'white' && isPlayerTurn) playerScore++;
              else if (obj.type === 'black' &&!isPlayerTurn) aiScore++;
              else if (obj.type === 'queen') {
                if (isPlayerTurn) playerScore += 3;
                else aiScore += 3;
              }
            }
          }
          else if (GAME_MODE === 'freestyle' || GAME_MODE === '2player') {
            pocketedThisTurn = true;
            if (obj.type === 'white') playerScore++;
            else if (obj.type === 'black') aiScore++;
            else if (obj.type === 'queen') {
              if (isPlayerTurn) playerScore += 3;
              else aiScore += 3;
            }
          }
        }
        updateScore();
      }
    });
  });

  let allObjects = [...coins.filter(c =>!c.pocketed), striker];
  for (let i = 0; i < allObjects.length; i++) {
    for (let j = i + 1; j < allObjects.length; j++) {
      let a = allObjects[i], b = allObjects[j];
      let dx = b.x - a.x, dy = b.y - a.y;
      let dist = Math.hypot(dx, dy);
      let minDist = a.radius + b.radius;

      if (dist < minDist && dist > 0) {
        let angle = Math.atan2(dy, dx);
        let overlap = minDist - dist;
        a.x -= Math.cos(angle) * overlap / 2;
        a.y -= Math.sin(angle) * overlap / 2;
        b.x += Math.cos(angle) * overlap / 2;
        b.y += Math.sin(angle) * overlap / 2;

        let v1 = Math.sqrt(a.vx * a.vx + a.vy * a.vy);
        let v2 = Math.sqrt(b.vx * b.vx + b.vy * b.vy);
        let dir1 = Math.atan2(a.vy, a.vx);
        let dir2 = Math.atan2(b.vy, b.vx);

        let vx1 = v2 * Math.cos(dir2 - angle);
        let vy1 = v1 * Math.sin(dir1 - angle);
        let vx2 = v1 * Math.cos(dir1 - angle);
        let vy2 = v2 * Math.sin(dir2 - angle);

        a.vx = Math.cos(angle) * vx1 + Math.cos(angle + Math.PI/2) * vy1;
        a.vy = Math.sin(angle) * vx1 + Math.sin(angle + Math.PI/2) * vy1;
        b.vx = Math.cos(angle) * vx2 + Math.cos(angle + Math.PI/2) * vy2;
        b.vy = Math.sin(angle) * vx2 + Math.sin(angle + Math.PI/2) * vy2;
      }
    }
  }

  return moving;
}

function updateScore() {
  if (playerScoreEl) playerScoreEl.textContent = playerScore;
  if (aiScoreEl) aiScoreEl.textContent = aiScore;

  let whiteLeft = coins.filter(c => c.type === 'white' &&!c.pocketed).length;
  let blackLeft = coins.filter(c => c.type === 'black' &&!c.pocketed).length;

  if (whiteLeft === 0 && playerScore > aiScore) {
    setTimeout(() => {
      const winner = GAME_MODE === '2player'? playerNames[0] : 'You';
      alert(`🎉 ${winner} Won!\nScore: ${playerScore} - ${aiScore}`);
      if (GAME_MODE === 'classic') {
        let coins = parseInt(localStorage.getItem('carromCoins') || '2500');
        coins += 180;
        localStorage.setItem('carromCoins', coins);
      }
    }, 500);
    gameActive = false;
  } else if (blackLeft === 0 && aiScore > playerScore) {
    setTimeout(() => {
      const winner = GAME_MODE === '2player'? playerNames[1] : 'AI';
      alert(`😔 ${winner} Won!\nScore: ${playerScore} - ${aiScore}`);
    }, 500);
    gameActive = false;
  }
}

function resetStrikerPosition() {
  striker.x = 200;
  striker.y = isPlayerTurn? BASELINE_Y_PLAYER : BASELINE_Y_AI;
  striker.vx = 0;
  striker.vy = 0;
}

function switchTurn() {
  if (!pocketedThisTurn &&!foulCommitted) {
    isPlayerTurn =!isPlayerTurn;
    if (turnIndicator) {
      if (GAME_MODE === '2player') {
        turnIndicator.textContent = isPlayerTurn? `${playerNames[0]}'s Turn` : `${playerNames[1]}'s Turn`;
      } else {
        turnIndicator.textContent = isPlayerTurn? 'Your Turn' : 'AI Turn';
      }
      turnIndicator.style.background = isPlayerTurn? '#ff6b35' : '#e63946';
    }
  }

  resetStrikerPosition();
  pocketedThisTurn = false;
  foulCommitted = false;
  hasShot = false;
  selectedCoin = null;

  if (!isPlayerTurn && gameActive && GAME_MODE!== '2player') {
    setTimeout(aiMove, 800);
  }
}

function aiMove() {
  if (isPlayerTurn ||!gameActive || aiThinking) return;
  aiThinking = true;
  aiStatus = 'AI is positioning...';

  let targets = coins.filter(c =>!c.pocketed && (c.type === 'black' || c.type === 'queen'));
  if (targets.length === 0) targets = coins.filter(c =>!c.pocketed);
  if (targets.length === 0) {
    aiThinking = false;
    return;
  }

  let bestTarget = null;
  let bestScore = -9999;
  let bestStrikerX = 200;
  let bestPocket = null;

  for (let testX = BASELINE_MIN_X; testX <= BASELINE_MAX_X; testX += 8) {
    targets.forEach(coin => {
      pockets.forEach(pocket => {
        let coinToPocket = Math.hypot(coin.x - pocket.x, coin.y - pocket.y);
        let strikerToCoin = Math.hypot(testX - coin.x, BASELINE_Y_AI - coin.y);

        let angle1 = Math.atan2(coin.y - BASELINE_Y_AI, coin.x - testX);
        let angle2 = Math.atan2(pocket.y - coin.y, pocket.x - coin.x);
        let angleDiff = Math.abs(angle1 - angle2);
        if (angleDiff > Math.PI) angleDiff = 2 * Math.PI - angleDiff;

        let score = 1000 - coinToPocket * 2 - strikerToCoin * 0.2 - angleDiff * 100;
        if (coin.type === 'queen') score += 500;
        if (angleDiff < 0.3) score += 200;
        if (coinToPocket < 80) score += 100;

        if (score > bestScore) {
          bestScore = score;
          bestTarget = coin;
          bestPocket = pocket;
          bestStrikerX = testX;
        }
      });
    });
  }

  striker.x = bestStrikerX;
  striker.y = BASELINE_Y_AI;

  setTimeout(() => {
    aiStatus = 'AI is aiming...';
    setTimeout(() => {
      if (bestTarget && bestPocket) {
        let angleToCoin = Math.atan2(bestTarget.y - striker.y, bestTarget.x - striker.x);
        let angleCoinToPocket = Math.atan2(bestPocket.y - bestTarget.y, bestPocket.x - bestTarget.x);
        let shootAngle = (angleToCoin + angleCoinToPocket) / 2;

        shootAngle += (Math.random() - 0.5) * 0.08;

        let dist = Math.hypot(bestTarget.x - striker.x, bestTarget.y - striker.y);
        let power = 4 + (dist / 100) * 4;
        power = Math.max(4, Math.min(8, power));

        striker.vx = Math.cos(shootAngle) * power;
        striker.vy = Math.sin(shootAngle) * power;
        hasShot = true;
      }
      aiThinking = false;
      aiStatus = '';
    }, 900);
  }, 700);
}

function gameLoop() {
  if (!ctx) return;
  drawBoard();
  drawCoins();
  drawStriker();

  let moving = updatePhysics();

  if (!moving && gameActive && hasShot) {
    hasShot = false;
    striker.vx = 0; striker.vy = 0;
    switchTurn();
  }

  requestAnimationFrame(gameLoop);
}

function handleStart(e) {
  if ((!isPlayerTurn && GAME_MODE!== '2player') ||!gameActive || hasShot || aiThinking) return;
  e.preventDefault();

  const pos = getCanvasPos(e);
  const distToStriker = Math.hypot(pos.x - striker.x, pos.y - striker.y);

  if (GAME_MODE === 'freestyle' && distToStriker > striker.radius + 50) {
    for (let coin of coins) {
      if (!coin.pocketed && Math.hypot(pos.x - coin.x, pos.y - coin.y) < coin.radius + 10) {
        selectedCoin = coin;
        return;
      }
    }
  }

  if (distToStriker < striker.radius + 50) {
    isDragging = true;
    isPositioning = false;
    dragStart = { x: pos.x, y: pos.y };
    dragCurrent = { x: pos.x, y: pos.y };
  }
  else if (pos.y > BASELINE_Y_PLAYER + 10 && pos.y < BASELINE_Y_PLAYER + 85 &&
           pos.x > BASELINE_MIN_X - 30 && pos.x < BASELINE_MAX_X + 30) {
    isDragging = true;
    isPositioning = true;
    dragStart = { x: pos.x, y: pos.y };
    dragCurrent = { x: pos.x, y: pos.y };
  }
}

function handleMove(e) {
  if (!gameActive ||!isDragging) return;
  e.preventDefault();

  const pos = getCanvasPos(e);

  if (isPositioning) {
    striker.x = Math.max(BASELINE_MIN_X, Math.min(BASELINE_MAX_X, pos.x));
    striker.y = isPlayerTurn? BASELINE_Y_PLAYER : BASELINE_Y_AI;
  } else {
    dragCurrent = { x: pos.x, y: pos.y };
  }
}

function handleEnd(e) {
  if (!isDragging) return;
  e.preventDefault();

  if (isPositioning) {
    isPositioning = false;
    isDragging = false;
    dragStart = null;
    dragCurrent = null;
    return;
  }

  isDragging = false;

  if (!dragStart ||!dragCurrent) {
    dragStart = null;
    dragCurrent = null;
    return;
  }

  const dx = dragCurrent.x - dragStart.x;
  const dy = dragCurrent.y - dragStart.y;
  const dragDist = Math.hypot(dx, dy);

  if (dragDist > 5) {
    const power = Math.min(dragDist / MAX_DRAG_DISTANCE, 1) * MAX_POWER;
    const shootAngle = Math.atan2(-dy, -dx);

    striker.vx = Math.cos(shootAngle) * power;
    striker.vy = Math.sin(shootAngle) * power;
    hasShot = true;
  }

  dragStart = null;
  dragCurrent = null;
}

if (canvas) {
  canvas.addEventListener('mousedown', handleStart);
  canvas.addEventListener('mousemove', handleMove);
  canvas.addEventListener('mouseup', handleEnd);

  canvas.addEventListener('touchstart', handleStart, { passive: false });
  canvas.addEventListener('touchmove', handleMove, { passive: false });
  canvas.addEventListener('touchend', handleEnd, { passive: false });
}

document.addEventListener('keydown', (e) => {
  if ((!isPlayerTurn && GAME_MODE!== '2player') ||!gameActive || hasShot) return;
  if (e.key === 'ArrowLeft') {
    striker.x = Math.max(BASELINE_MIN_X, striker.x - 10);
  } else if (e.key === 'ArrowRight') {
    striker.x = Math.min(BASELINE_MAX_X, striker.x + 10);
  }
});

if (resetBtn) {
  resetBtn.addEventListener('click', () => {
    initCoins();
    striker.x = 200; striker.y = BASELINE_Y_PLAYER; striker.vx = 0; striker.vy = 0;
    playerScore = 0; aiScore = 0; isPlayerTurn = true; gameActive = true; hasShot = false; aiThinking = false;
    selectedCoin = null;
    updateScore();
    if (turnIndicator) {
      if (GAME_MODE === '2player') {
        turnIndicator.textContent = `${playerNames[0]}'s Turn`;
      } else {
        turnIndicator.textContent = 'Your Turn';
      }
      turnIndicator.style.background = '#ff6b35';
    }
  });
}

if (backBtn) {
  backBtn.addEventListener('click', () => {
    window.location.href = '/storage/emulated/0/MINIGRAM1/Games/carrom/carrom_mode/med.html';
  });
}

if (settingsBtn) {
  settingsBtn.addEventListener('click', () => {
    alert('Settings\n🔊 Sound: ON\n📳 Vibration: ON\n\nComing Soon!');
  });
}

initCoins();
setupPlayerNames();
if (ctx) gameLoop();
```

---

Generated by MiniGram MD Intelligence V6.

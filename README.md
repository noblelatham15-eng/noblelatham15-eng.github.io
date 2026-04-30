<!doctype html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SGA Campaign Clash</title>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body {
  height: 100%;
  width: 100%;
  font-family: 'Trebuchet MS', sans-serif;
  background: linear-gradient(135deg, #0b1f3a 0%, #132f57 100%);
  color: #fff;
  overflow: hidden;
}

#app {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
  padding-bottom: 100px;
  overflow-y: auto;
}

.container {
  max-width: 500px;
  width: 100%;
  background: rgba(20, 30, 50, 0.9);
  border: 3px solid #f4c542;
  border-radius: 20px;
  padding: 30px;
  box-shadow: 0 8px 32px rgba(244, 197, 66, 0.3);
}

h1 {
  color: #f4c542;
  font-size: 42px;
  margin-bottom: 8px;
  text-shadow: 0 0 20px rgba(244, 197, 66, 0.5);
  text-align: center;
}

h2 {
  color: #f4c542;
  font-size: 20px;
  text-align: center;
  margin-bottom: 20px;
  font-weight: 600;
}

.subtitle {
  text-align: center;
  color: #b0b0b0;
  font-size: 14px;
  margin-bottom: 30px;
  line-height: 1.5;
}

.input-group {
  margin-bottom: 20px;
}

input {
  width: 100%;
  padding: 14px;
  margin-top: 8px;
  border: 2px solid #f4c542;
  border-radius: 10px;
  font-size: 15px;
  background: rgba(255, 255, 255, 0.95);
  color: #0b1f3a;
  font-family: inherit;
}

label {
  display: block;
  color: #f4c542;
  font-weight: 600;
  font-size: 13px;
}

button {
  width: 100%;
  padding: 14px;
  margin: 12px 0;
  border: none;
  border-radius: 12px;
  font-size: 15px;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.btn-primary {
  background: #f4c542;
  color: #0b1f3a;
  box-shadow: 0 4px 15px rgba(244, 197, 66, 0.3);
}

.btn-primary:hover {
  background: #ffe07a;
  transform: translateY(-2px);
}

.card-content {
  background: rgba(255, 255, 255, 0.05);
  border-left: 4px solid #f4c542;
  padding: 16px;
  margin: 16px 0;
  border-radius: 8px;
  line-height: 1.6;
  font-size: 14px;
}

.secret-code {
  font-size: 52px;
  letter-spacing: 8px;
  color: #f4c542;
  font-weight: bold;
  font-family: 'Courier New', monospace;
  text-align: center;
  margin: 20px 0;
}

.battle-arena {
  background: linear-gradient(180deg, #1a3a52 0%, #0f2337 100%);
  border: 4px solid #f4c542;
  border-radius: 20px;
  padding: 20px;
  margin-bottom: 20px;
}

.battle-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 18px;
  font-weight: bold;
  color: #f4c542;
  font-size: 14px;
}

.battle-level {
  background: rgba(244, 197, 66, 0.2);
  padding: 8px 12px;
  border-radius: 6px;
  border: 2px solid #f4c542;
}

.opponent-section,
.player-section {
  text-align: center;
  margin: 20px 0;
}

.opponent-name {
  font-size: 16px;
  color: #ef4444;
  font-weight: bold;
}

.player-name {
  font-size: 16px;
  color: #4ade80;
  font-weight: bold;
}

.opponent-sprite,
.player-sprite {
  font-size: 80px;
  margin: 10px 0;
  animation: float 2s ease-in-out infinite;
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

.hp-container,
.hp-container-player {
  background: rgba(0, 0, 0, 0.4);
  border-radius: 8px;
  padding: 8px;
  margin: 8px 0;
}

.hp-container {
  border: 2px solid #ef4444;
}

.hp-container-player {
  border: 2px solid #4ade80;
}

.hp-label {
  display: flex;
  justify-content: space-between;
  font-size: 12px;
  margin-bottom: 4px;
}

.hp-bar {
  background: #1a1a1a;
  border: 1px solid #666;
  border-radius: 4px;
  height: 18px;
  overflow: hidden;
}

.hp-fill {
  background: linear-gradient(90deg, #ef4444, #ff6b6b);
  height: 100%;
  transition: width 0.5s ease;
}

.hp-fill-player {
  background: linear-gradient(90deg, #4ade80, #86efac);
  height: 100%;
  transition: width 0.5s ease;
}

.dialogue-box {
  background: rgba(0, 0, 0, 0.8);
  border: 3px solid #f4c542;
  border-radius: 12px;
  padding: 16px;
  margin: 20px 0;
  min-height: 60px;
  text-align: center;
  font-weight: bold;
  color: #f4c542;
}

.move-button {
  background: linear-gradient(135deg, #7c3aed 0%, #6d28d9 100%);
  color: #fff;
  border: 2px solid #a78bfa;
  text-align: left;
  padding: 14px;
  font-weight: 600;
  margin: 8px 0;
}

.move-button:hover {
  background: linear-gradient(135deg, #a78bfa 0%, #8b5cf6 100%);
  transform: translateX(4px);
}

.feedback-message {
  background: rgba(244, 197, 66, 0.15);
  border: 2px solid #f4c542;
  border-radius: 8px;
  padding: 16px;
  margin: 16px 0;
  font-weight: bold;
  text-align: center;
}

.super-effective {
  color: #4ade80;
  text-shadow: 0 0 10px #4ade80;
  font-size: 20px;
}

.weak-hit {
  color: #fbbf24;
  text-shadow: 0 0 10px #fbbf24;
  font-size: 18px;
}

.counterattack {
  color: #ef4444;
  text-shadow: 0 0 10px #ef4444;
  font-size: 18px;
}

.ticker-bottom {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  height: 80px;
  background: #050505;
  border-top: 4px solid #ef4444;
  z-index: 99;
  font-weight: bold;
  font-size: 12px;
}

.breaking-bar {
  background: #ef4444;
  padding: 6px 12px;
}

.ticker-scroll {
  overflow: hidden;
  padding: 8px 12px;
  white-space: nowrap;
  color: #f4c542;
}

.ticker-scroll span {
  display: inline-block;
  animation: scroll 20s linear infinite;
}

@keyframes scroll {
  0% { transform: translateX(100%); }
  100% { transform: translateX(-100%); }
}

.ticker-logo {
  position: absolute;
  right: 12px;
  bottom: 8px;
  font-size: 11px;
  color: #888;
}

.results-grid {
  display: grid;
  gap: 12px;
  margin: 20px 0;
}

.result-item {
  background: rgba(244, 197, 66, 0.1);
  border: 2px solid #f4c542;
  border-radius: 8px;
  padding: 12px;
  text-align: center;
}

.result-item strong {
  color: #f4c542;
  display: block;
  font-size: 18px;
}
</style>
</head>

<body>
<div id="app"></div>

<div class="ticker-bottom">
  <div class="breaking-bar">BREAKING NEWS</div>
  <div class="ticker-scroll">
    <span>🗳️ Campaign in progress — Vote for your choice! &nbsp;&nbsp;&nbsp; Vote today! &nbsp;&nbsp;&nbsp; The future is in your hands! &nbsp;&nbsp;&nbsp;</span>
  </div>
  <div class="ticker-logo">SGA DAILY • VOTE NOW</div>
</div>

<script>
const votingLink = "https://docs.google.com/forms/d/e/1FAIpQLSccZfRkC27QGu8XxWtbDqbgzhXgJ4hendn9ijGNiPVDbRg87w/viewform?pli=1";
const issuesLink = "https://docs.google.com/forms/d/e/1FAIpQLSdQTmekhe8C7lKV4uplRaacaNRfk6OTy-kF4zUG45QJqkWCrA/viewform?usp=publish-editor";

let playerName = "";
let selectedRole = "";
let round = 0;
let playerScore = 0;
let crowdResistance = 100;
let history = [];

const roleSprites = {
  "President": "👔",
  "Vice President": "📊",
  "Treasurer": "💰",
  "Secretary": "📝"
};

const crowdSprites = ["😕", "😤", "😠", "🤨", "😡"];

const campaigns = {
  "President": {
    questions: [
      {
        q: "You have missed two meetings, and the team is confused. What do you do?",
        options: [
          { text: "Use Accountability: Apologize, ask for updates, and reset the plan.", points: 20, feedback: "Strong move — you owned the issue and rebuilt trust!" },
          { text: "Use Command Bluff: Pretend nothing happened and start giving orders.", points: 0, feedback: "Failed! You skipped accountability." },
          { text: "Use Retreat: Let someone else lead because you feel embarrassed.", points: 10, feedback: "Partial block — safe but weak leadership." }
        ]
      },
      {
        q: "A major event is behind schedule. People are waiting on your decision.",
        options: [
          { text: "Use Clear Decision: Make a clear decision after reviewing key facts.", points: 20, feedback: "Super effective! Leaders act with clarity." },
          { text: "Use Delay Tactic: Postpone the decision until everyone agrees.", points: 10, feedback: "It worked, but consensus slows progress." },
          { text: "Use Avoidance: Ignore the issue until the next meeting.", points: 0, feedback: "Failed! Avoidance creates bigger problems." }
        ]
      },
      {
        q: "Two team members disagree publicly.",
        options: [
          { text: "Use Team Redirect: Pause the argument and bring focus back to the mission.", points: 20, feedback: "Super effective! You turned conflict into purpose." },
          { text: "Use Favoritism: Pick the person you like more.", points: 0, feedback: "Failed! Favoritism destroys trust." },
          { text: "Use Dodge: Tell them to figure it out alone.", points: 10, feedback: "Partial block — you avoided helping resolve conflict." }
        ]
      },
      {
        q: "The popular choice is not the responsible choice.",
        options: [
          { text: "Use Integrity: Explain the responsible choice and offer a compromise.", points: 20, feedback: "Super effective! You balanced honesty and leadership." },
          { text: "Use Popularity Move: Choose popularity over responsibility.", points: 0, feedback: "Failed! Popularity should not lead the mission." },
          { text: "Use Silent Decision: Make the right choice but refuse to explain it.", points: 10, feedback: "Partial block — right decisions still need communication." }
        ]
      },
      {
        q: "The team is tired, frustrated, and close to quitting.",
        options: [
          { text: "Use Rally Cry: Encourage them, simplify the plan, and lead by example.", points: 20, feedback: "Super effective! You restored morale through action." },
          { text: "Use Blame Shift: Tell them failure is not your fault.", points: 0, feedback: "Failed! Blame weakens leadership." },
          { text: "Use Push Harder: Keep pushing without listening.", points: 10, feedback: "Partial block — effort matters, but listening matters too." }
        ]
      }
    ]
  },

  "Vice President": {
    questions: [
      {
        q: "The President is absent and people look to you.",
        options: [
          { text: "Use Step Up: Organize the group and keep the mission moving.", points: 20, feedback: "Super effective! Leadership is service, not just title." },
          { text: "Use Pass the Buck: Say it is not your responsibility.", points: 0, feedback: "Failed! You abandoned the team." },
          { text: "Use Wait and See: Hope quietly that someone else leads.", points: 10, feedback: "Partial block — safe, but not courageous." }
        ]
      },
      {
        q: "You notice the President is overwhelmed.",
        options: [
          { text: "Use Support Shield: Support them privately and help stabilize the team.", points: 20, feedback: "Super effective! You supported with maturity." },
          { text: "Use Public Critique: Criticize them publicly.", points: 0, feedback: "Failed! Public criticism creates division." },
          { text: "Use Silent Takeover: Take over without speaking to them.", points: 10, feedback: "Partial block — helpful, but disrespectful." }
        ]
      },
      {
        q: "A team member is being ignored.",
        options: [
          { text: "Use Inclusion Call: Bring their concern into the discussion respectfully.", points: 20, feedback: "Super effective! You protected fairness and inclusion." },
          { text: "Use Silence: Stay silent to avoid tension.", points: 10, feedback: "Partial block — silence keeps the problem alive." },
          { text: "Use Dismiss: Tell them their idea does not matter.", points: 0, feedback: "Failed! Dismissiveness kills morale." }
        ]
      },
      {
        q: "The team is divided over a decision.",
        options: [
          { text: "Use Unity Focus: Guide the team back to facts, goals, and fairness.", points: 20, feedback: "Super effective! You brought structure to conflict." },
          { text: "Use Volume Vote: Side with the loudest group.", points: 0, feedback: "Failed! Volume is not wisdom." },
          { text: "Use Avoidance: Skip the meeting.", points: 10, feedback: "Partial block — avoidance delays the problem." }
        ]
      },
      {
        q: "You must lead even though you feel uncomfortable.",
        options: [
          { text: "Use Courage Break: Step out of your comfort zone and serve.", points: 20, feedback: "Super effective! Courage is leadership in action." },
          { text: "Use Title Shield: Refuse because you are not the President.", points: 0, feedback: "Failed! You hid behind your title." },
          { text: "Use Minimum Effort: Do only the bare minimum.", points: 10, feedback: "Partial block — minimum effort rarely inspires people." }
        ]
      }
    ]
  },

  "Treasurer": {
    questions: [
      {
        q: "The team wants to spend most of the budget on decorations.",
        options: [
          { text: "Use Budget Balance: Create a balanced spending plan.", points: 20, feedback: "Super effective! You protected the whole mission." },
          { text: "Use Excitement Yield: Approve it because everyone is excited.", points: 0, feedback: "Failed! Excitement does not replace planning." },
          { text: "Use Full Block: Refuse to spend any money.", points: 10, feedback: "Partial block — protection without balance hurts morale." }
        ]
      },
      {
        q: "You find a small budget mistake.",
        options: [
          { text: "Use Transparency: Report it honestly and correct it.", points: 20, feedback: "Super effective! Integrity builds trust." },
          { text: "Use Silent Fix: Fix it quietly and tell no one.", points: 10, feedback: "Partial block — correction matters, but transparency too." },
          { text: "Use Ignore: Let it pass without action.", points: 0, feedback: "Failed! Small errors become big problems." }
        ]
      },
      {
        q: "Someone pressures you to approve an expense quickly.",
        options: [
          { text: "Use Due Diligence: Ask for receipts, purpose, and budget impact first.", points: 20, feedback: "Super effective! You used wisdom before approval." },
          { text: "Use Pressure Yield: Approve it to avoid drama.", points: 0, feedback: "Failed! Pressure should not control money." },
          { text: "Use Delay Defense: Postpone everything without explanation.", points: 10, feedback: "Partial block — delay needs communication." }
        ]
      },
      {
        q: "A popular idea costs too much.",
        options: [
          { text: "Use Smart No: Say no and offer a cheaper alternative.", points: 20, feedback: "Super effective! You protected money and morale." },
          { text: "Use Hope Gamble: Say yes and hope money appears later.", points: 0, feedback: "Failed! Hope is not a budget plan." },
          { text: "Use No Explanation: Say no without explaining why.", points: 10, feedback: "Partial block — answer right, but communication missing." }
        ]
      },
      {
        q: "The team is upset because you are protecting the budget.",
        options: [
          { text: "Use Teach: Explain the numbers clearly and connect them to the mission.", points: 20, feedback: "Super effective! You taught why money matters." },
          { text: "Use Defensive Strike: Get defensive and argue.", points: 0, feedback: "Failed! Defensiveness breaks trust." },
          { text: "Use Withdrawal: Stop participating.", points: 10, feedback: "Partial block — withdrawal does not solve conflict." }
        ]
      }
    ]
  },

  "Secretary": {
    questions: [
      {
        q: "Meeting notes are unclear and people are confused.",
        options: [
          { text: "Use Clarity Rebuild: Remake the notes with action items and deadlines.", points: 20, feedback: "Super effective! Clarity creates progress." },
          { text: "Use Repeat Confusion: Send the same unclear notes again.", points: 0, feedback: "Failed! Repeated confusion is still confusion." },
          { text: "Use Reactive Wait: Wait until someone asks for clarification.", points: 10, feedback: "Partial block — reactive communication is not enough." }
        ]
      },
      {
        q: "You missed part of the meeting.",
        options: [
          { text: "Use Ask & Verify: Ask for clarification and send accurate updates.", points: 20, feedback: "Super effective! Accuracy protects the team." },
          { text: "Use Guess Gamble: Guess what happened.", points: 0, feedback: "Failed! Guessing creates misinformation." },
          { text: "Use Skip: Ignore the notes completely.", points: 10, feedback: "Partial block — skipping communication leaves gaps." }
        ]
      },
      {
        q: "The team keeps forgetting deadlines.",
        options: [
          { text: "Use Reminder System: Create a simple reminder system.", points: 20, feedback: "Super effective! You solved the real problem." },
          { text: "Use Blame Blast: Blame everyone for forgetting.", points: 0, feedback: "Failed! Blame does not build systems." },
          { text: "Use Single Mention: Mention it once and move on.", points: 10, feedback: "Partial block — reminders need consistency." }
        ]
      },
      {
        q: "You are overwhelmed but still responsible for communication.",
        options: [
          { text: "Use Progress Over Perfect: Send partial updates now, confirm details later.", points: 20, feedback: "Super effective! Progress beats silence." },
          { text: "Use Perfection Wait: Say nothing until everything is perfect.", points: 10, feedback: "Partial block — perfection can delay action." },
          { text: "Use Communication Stop: Stop communicating completely.", points: 0, feedback: "Failed! Silence creates confusion." }
        ]
      },
      {
        q: "A mistake in communication caused confusion.",
        options: [
          { text: "Use Accountability: Take responsibility, correct the message, and prevent repeats.", points: 20, feedback: "Super effective! You modeled accountability." },
          { text: "Use Team Blame: Blame the team.", points: 0, feedback: "Failed! Blame destroys trust." },
          { text: "Use Ignore Embarrassment: Ignore it because it is embarrassing.", points: 10, feedback: "Partial block — avoidance keeps the mistake alive." }
        ]
      }
    ]
  }
};

function showHome() {
  document.getElementById("app").innerHTML = `
    <div class="container">
      <h1>⭐ SGA Battle Arena ⭐</h1>
      <h2>Leadership Challenge</h2>

      <div class="subtitle">
        Step into the SGA Battle Arena and test your leadership skills.
        Choose your role, face the crowd, and make the right decisions through 5 levels.
      </div>

      <div class="card-content">
        <strong>How to Play:</strong><br><br>
        The crowd will challenge your leadership.<br>
        Each choice is a leadership move.<br>
        Strong choices help you win the battle.<br>
        Weak choices make the battle harder.<br><br>
        Choose wisely. Your leadership is being tested.
      </div>

      <div class="input-group">
        <label>Your Name:</label>
        <input type="text" id="playerName" placeholder="Enter your name" maxlength="20">
      </div>

      <button class="btn-primary" onclick="showRoleStart()">Start Game</button>
    </div>
  `;
}

function showRoleStart() {
  playerName = document.getElementById("playerName").value.trim();

  if (!playerName) {
    alert("Please enter your name!");
    return;
  }

  document.getElementById("app").innerHTML = `
    <div class="container">
      <h1>Choose Your Role</h1>
      <h2>Who will you lead as?</h2>

      <div class="subtitle">
        Each role has different leadership challenges.
        Pick your position and enter the battle.
      </div>

      <button class="btn-primary" onclick="selectRoleAndStart('President')">👔 President</button>
      <button class="btn-primary" onclick="selectRoleAndStart('Vice President')">📊 Vice President</button>
      <button class="btn-primary" onclick="selectRoleAndStart('Treasurer')">💰 Treasurer</button>
      <button class="btn-primary" onclick="selectRoleAndStart('Secretary')">📝 Secretary</button>
    </div>
  `;
}

function selectRoleAndStart(role) {
  selectedRole = role;
  round = 0;
  playerScore = 0;
  crowdResistance = 100;
  history = [];
  showBattleScreen();
}

function showBattleScreen() {
  const data = campaigns[selectedRole];
  const q = data.questions[round];
  const crowdSprite = crowdSprites[Math.min(round, crowdSprites.length - 1)];

  const movesHTML = q.options
    .map((opt, i) => `<button class="move-button" onclick="executeMove(${i})">${opt.text}</button>`)
    .join("");

  document.getElementById("app").innerHTML = `
    <div class="container">
      <div class="battle-arena">
        <div class="battle-header">
          <div class="battle-level">Level ${round + 1} / 5</div>
          <div>Score: <strong style="color:#4ade80;">${playerScore}</strong></div>
        </div>

        <div class="opponent-section">
          <div class="opponent-name">🎭 The Crowd 🎭</div>
          <div class="opponent-sprite">${crowdSprite}</div>
          <div class="hp-container">
            <div class="hp-label">
              <span>Crowd Doubt</span>
              <span>${crowdResistance}%</span>
            </div>
            <div class="hp-bar">
              <div class="hp-fill" style="width:${crowdResistance}%;"></div>
            </div>
          </div>
        </div>

        <div class="player-section">
          <div class="player-name">${roleSprites[selectedRole]} ${playerName} (${selectedRole})</div>
          <div class="player-sprite">${roleSprites[selectedRole]}</div>
          <div class="hp-container-player">
            <div class="hp-label">
              <span>Leadership Power</span>
              <span>${playerScore} / 100</span>
            </div>
            <div class="hp-bar">
              <div class="hp-fill-player" style="width:${playerScore}%;"></div>
            </div>
          </div>
        </div>
      </div>

      <div class="dialogue-box">
        ⚔️ The Crowd challenges: "${q.q}" ⚔️
      </div>

      ${movesHTML}
    </div>
  `;
}

function executeMove(optionIdx) {
  const data = campaigns[selectedRole];
  const q = data.questions[round];
  const option = q.options[optionIdx];

  playerScore += option.points;
  crowdResistance = Math.max(0, crowdResistance - (option.points / 20) * 25);

  const symbol =
    option.points === 20 ? "✓ SUPER EFFECTIVE!" :
    option.points === 10 ? "⚡ It worked... but barely!" :
    "✗ THE CROWD COUNTERED!";

  const msgClass =
    option.points === 20 ? "super-effective" :
    option.points === 10 ? "weak-hit" :
    "counterattack";

  history.push({
    round: round + 1,
    question: q.q,
    move: option.text,
    points: option.points,
    feedback: option.feedback
  });

  showBattleFeedback(symbol, msgClass, option.feedback, option.points);
}

function showBattleFeedback(symbol, msgClass, feedback, points) {
  document.getElementById("app").innerHTML = `
    <div class="container">
      <div class="feedback-message">
        <div class="${msgClass}">${symbol}</div>
      </div>

      <div class="card-content">
        <strong>Points earned: ${points}</strong><br>
        ${feedback}
      </div>

      <button class="btn-primary" onclick="nextRound()">Continue</button>
    </div>
  `;
}

function nextRound() {
  round++;
  if (round < 5) {
    showBattleScreen();
  } else {
    showBattleResult();
  }
}

function showBattleResult() {
  const won = playerScore >= 70;
  const code = won ? "215" : "223";

  const libraryMessage = won
    ? "Head to the Library to receive a prize hidden in the English dictionary with a gold tassel."
    : "Head to the Library to receive a prize hidden in the English dictionary.";

  const badge =
    playerScore >= 90 ? "Elite Leader" :
    playerScore >= 70 ? "Strong Leader" :
    playerScore >= 40 ? "Developing Leader" :
    "Needs Practice";

  document.getElementById("app").innerHTML = `
    <div class="container">
      <h1>${won ? "🎉 VICTORY! 🎉" : "⚠️ BATTLE LOST ⚠️"}</h1>

      <div class="results-grid">
        <div class="result-item">
          <strong>${playerScore}</strong>
          <span>Final Score</span>
        </div>

        <div class="result-item">
          <strong>${badge}</strong>
          <span>Leadership Status</span>
        </div>
      </div>

      <div class="secret-code">${code}</div>

      <div class="card-content">
        <strong>${libraryMessage}</strong>
        <p style="margin-top:8px;">
          ${won
            ? "You showed strong leadership, accountability, and wisdom under pressure. Congratulations!"
            : "You showed promise, but the crowd overpowered you. Try again and sharpen your leadership moves!"}
        </p>
      </div>

      <button class="btn-primary" onclick="showReview()">📋 Review My Moves</button>
      <button class="btn-primary" onclick="showHome()">🔄 New Battle</button>
      <button class="btn-primary" onclick="window.open(votingLink, '_blank')">🗳️ Vote Here</button>
      <button class="btn-primary" onclick="window.open(issuesLink, '_blank')">💭 Submit Questions</button>
    </div>
  `;
}

function showReview() {
  let reviewHTML = `<div class="container"><h2>⚔️ Battle Review ⚔️</h2>`;

  history.forEach(h => {
    const icon = h.points === 20 ? "✓" : h.points === 10 ? "⚡" : "✗";
    reviewHTML += `
      <div class="card-content">
        <strong>Level ${h.round}: ${icon} +${h.points} points</strong><br>
        Q: ${h.question}<br>
        Move: ${h.move}<br>
        ${h.feedback}
      </div>
    `;
  });

  reviewHTML += `<button class="btn-primary" onclick="showBattleResult()">Back to Results</button></div>`;
  document.getElementById("app").innerHTML = reviewHTML;
}

showHome();
</script>
</body>
</html>

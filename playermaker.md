---
layout: none
permalink: /player
---
{% include chess_head.html %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Manage Players</title>
    <style>
        body {
            background: linear-gradient(to bottom, #ffff99, #ffcc66);
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        input, button {
            display: block;
            margin: 10px auto;
            padding: 10px;
            font-size: 16px;
        }
        button {
            cursor: pointer;
        }
        .player-controls {
            display: flex;
            justify-content: center;
            gap: 5px;
            margin-top: 10px;
        }
        .pairs-list {
            margin-top: 20px;
        }
        .player {
            margin-bottom: 20px;
        }
        .player-info {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        .player-info div {
            margin: 0 5px;
        }
    </style>
</head>
<body>
    <h1>Manage Players</h1>
    <div>
        <label for="playerName">Player Name</label>
        <input type="text" id="playerName" placeholder="Player Name">
    </div>
    <div>
        <label for="divisionNumber">Division #</label>
        <input type="number" id="divisionNumber" placeholder="Division #">
    </div>
    <button id="addPlayerButton">Add Player</button>
    <button id="getAllPlayersButton">Get All Players</button>
    <button id="clearAllButton">Clear All Players</button>
    <button id="pairPlayerButton">Pair Players</button>
    <div id="playersList"></div>
    <div class="pairs-list" id="pairsList"></div>
</body>
</html>

<script>
var deployed = "https://dnhs-chess-backend.onrender.com/";
var local = "http://localhost:8085/"
var url = deployed;
document.getElementById('addPlayerButton').addEventListener('click', addPlayer);
document.getElementById('getAllPlayersButton').addEventListener('click', getAllPlayers);
document.getElementById('clearAllButton').addEventListener('click', clearAllPlayers);
document.getElementById('pairPlayerButton').addEventListener('click', pairPlayers);

async function pairPlayers() {
    try {
        const response = await fetch(url + 'leaderboard/pairPlayers', {
            method: 'GET',
        });
        
        if (response.ok) {
            const pairs = await response.json();
            displayPairs(pairs);
        } else {
            alert('Failed to pair players');
        }
    } catch (error) {
        alert('Error: ' + error.message);
    }
}

function displayPairs(pairs) {
    const pairsList = document.getElementById('pairsList');
    pairsList.innerHTML = '<h1>Pairs</h1>';

    if (!pairs || pairs.length === 0) {
        pairsList.innerHTML = '<p>No pairs found</p>';
        return;
    }

    pairs.forEach(pair => {
        const pairDiv = document.createElement('div');
        pairDiv.innerHTML = `Pair: ${pair.player1.name} vs ${pair.player2.name}`;
        //pairDiv.innerHTML = `Pair: ${pair.player1.name} (Score: ${pair.player1.score}) vs ${pair.player2.name} (Score: ${pair.player2.score})`;
        pairsList.appendChild(pairDiv);
    });
}

async function addPlayer() {
    const playerName = document.getElementById('playerName').value;
    const divisionNumber = parseInt(document.getElementById('divisionNumber').value);
    
    if (!playerName || isNaN(divisionNumber)) {
        alert('Please provide valid player name and division number.');
        return;
    }
    
    const player = {
        name: playerName,
        divisionNumber: divisionNumber,
        score: 0
    };
    
    try {
        const response = await fetch(url + 'leaderboard/add', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify(player),
        });
        
        if (response.ok) {
            alert('Player added successfully');
            document.getElementById('playerName').value = '';
            document.getElementById('divisionNumber').value = '';
            getAllPlayers(); // Refresh the player list
        } else {
            const errorMessage = await response.text();
            alert('Failed to add player: ' + errorMessage);
        }
    } catch (error) {
        alert('Error: ' + error.message);
    }
}

async function getAllPlayers() {
    try {
        const response = await fetch(url + 'leaderboard/allPlayers', {
            method: 'GET',
        });
        
        if (response.ok) {
            const playersByDivision = await response.json();
            displayPlayers(playersByDivision);
        } else {
            alert('Failed to fetch players');
        }
    } catch (error) {
        alert('Error: ' + error.message);
    }
}

async function clearAllPlayers() {
    try {
        const response = await fetch(url + 'leaderboard/removeAll', {
            method: 'DELETE',
        });
        
        if (response.ok) {
            alert('All players cleared successfully');
            getAllPlayers(); // Refresh the player list
        } else {
            alert('Failed to clear players');
        }
    } catch (error) {
        alert('Error: ' + error.message);
    }
}

async function deletePlayer(playerName) {
    try {
        const response = await fetch(url + `/leaderboard/remove?name=${encodeURIComponent(playerName)}`, {
            method: 'DELETE',
        });
        
        if (response.ok) {
            alert('Player deleted successfully');
            getAllPlayers(); // Refresh the player list
        } else {
            const errorMessage = await response.text();
            alert('Failed to delete player: ' + errorMessage);
        }
    } catch (error) {
        alert('Error: ' + error.message);
    }
}

function displayPlayers(playersByDivision) {
    const playersList = document.getElementById('playersList');
    playersList.innerHTML = '';

    if (!playersByDivision || playersByDivision.length === 0) {
        playersList.innerHTML = '<p>No players found</p>';
        return;
    }

    playersByDivision.forEach((division, index) => {
        if (division.length > 0) {
            const divisionHeader = document.createElement('h2');
            divisionHeader.textContent = `Division ${index + 1}`;
            playersList.appendChild(divisionHeader);

            division.forEach(player => {
                const playerDiv = document.createElement('div');
                playerDiv.className = 'player';
                playerDiv.innerHTML = `
                    <div class="player-info">
                        <div>Name: ${player.name}, Division: ${player.divisionNumber}, Score: ${player.score || 'N/A'}</div>
                        <div class="player-controls">
                            <button onclick="updateScore('${player.name}', 2)">Win</button>
                            <button onclick="updateScore('${player.name}', 1)">Draw</button>
                            <button onclick="updateScore('${player.name}', 0)">Lose</button>
                            <button onclick="deletePlayer('${player.name}')">Delete</button>
                        </div>
                    </div>
                `;
                playersList.appendChild(playerDiv);
            });
        }
    });
}

async function updateScore(playerName, points) {
    try {
        const response = await fetch(url + 'leaderboard/updateScore', {
            method: 'PATCH',
            headers: {
                'Content-Type': 'application/json',
                'Accept': 'application/json'
            },
            body: JSON.stringify({ name: playerName, points: points }),
        });

        if (response.ok) {
            alert('Score updated successfully');
            getAllPlayers(); // Refresh the player list
        } else {
            const errorMessage = await response.text();
            alert('Failed to update score: ' + errorMessage);
        }
    } catch (error) {
        alert('Error: ' + error.message);
    }
}
</script>

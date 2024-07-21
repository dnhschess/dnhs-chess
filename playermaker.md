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
            gap: 10px;
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
    <div id="playersList"></div>
</body>
</html>

<script>
document.getElementById('addPlayerButton').addEventListener('click', addPlayer);
document.getElementById('getAllPlayersButton').addEventListener('click', getAllPlayers);
document.getElementById('clearAllButton').addEventListener('click', clearAllPlayers);

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
        const response = await fetch('http://localhost:8085/leaderboard/add', {
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
        const response = await fetch('http://localhost:8085/leaderboard/allPlayers', {
            method: 'GET',
        });
        
        if (response.ok) {
            const players = await response.json();
            displayPlayers(players);
        } else {
            alert('Failed to fetch players');
        }
    } catch (error) {
        alert('Error: ' + error.message);
    }
}

async function clearAllPlayers() {
    try {
        const response = await fetch('http://localhost:8085/leaderboard/removeAll', {
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
        const response = await fetch(`http://localhost:8085/leaderboard/remove?name=${encodeURIComponent(playerName)}`, {
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

function displayPlayers(players) {
    const playersList = document.getElementById('playersList');
    playersList.innerHTML = '';
    
    if (players.length === 0) {
        playersList.innerHTML = '<p>No players found</p>';
        return;
    }
    
    players.forEach(player => {
        const playerDiv = document.createElement('div');
        playerDiv.innerHTML = `
            Name: ${player.name}, Division: ${player.divisionNumber}, Score: ${player.score || 'N/A'}
            <div class="player-controls">
                <button onclick="updateScore('${player.name}', 2)">Win</button>
                <button onclick="updateScore('${player.name}', 1)">Draw</button>
                <button onclick="updateScore('${player.name}', 0)">Lose</button>
                <button onclick="deletePlayer('${player.name}')">Delete</button>
            </div>
        `;
        playersList.appendChild(playerDiv);
    });
}

async function updateScore(playerName, points) {
    try {
        const response = await fetch(`http://localhost:8085/leaderboard/updateScore`, {
            method: 'PATCH',
            headers: {
                'Content-Type': 'application/json',
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

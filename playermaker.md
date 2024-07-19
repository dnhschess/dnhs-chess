---
layout: none
permalink: /player
---
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
    <div id="playersList"></div>
</body>
</html>

<script>
document.getElementById('addPlayerButton').addEventListener('click', addPlayer);
document.getElementById('getAllPlayersButton').addEventListener('click', getAllPlayers);

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

function displayPlayers(players) {
    const playersList = document.getElementById('playersList');
    playersList.innerHTML = '';
    
    if (players.length === 0) {
        playersList.innerHTML = '<p>No players found</p>';
        return;
    }
    
    players.forEach(player => {
        const playerDiv = document.createElement('div');
        playerDiv.textContent = `Name: ${player.name}, Division: ${player.divisionNumber}, Score: ${player.score || 'N/A'}`;
        playersList.appendChild(playerDiv);
    });
}

</script>
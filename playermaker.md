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
    <button id="pairPlayerButton">Pair Players</button>
    <div id="playersList"></div>
</body>
</html>

<script>
var deployed = "https://dnhs-chess-backend.onrender.com/";
var local = "http://localhost:8085/"
var url = deployed;
document.getElementById('addPlayerButton').addEventListener('click', addPlayer);
document.getElementById('getAllPlayersButton').addEventListener('click', getAllPlayers);
document.getElementById('clearAllButton').addEventListener('click', clearAllPlayers);
document.getElementById('pairPlayerButton').addEventListener('click', pairPlayerButton);

async function pairPlayerButton() {
    //alert('Pairing players...')
    const PlayerList = [
        { name: 'Alice', score: 30 },
        { name: 'Bob', score: 25 },
        { name: 'Zoe', score: 20 },
        { name: 'Maggie', score: 21 },
        { name: 'Jay', score: 19 },
        { name: 'Charlie', score: 35 }];
    //alert('Player #2: ' + PlayerList[1].name);

    const PlayerScoreDifference = [];
    var index_PlayersPaired = []

    for (let i = 0; i < PlayerList.length; i++) {
        if  ( !(index_PlayersPaired.includes(i)) ) {
            alert('Player: ' + i + ' Name: ' + PlayerList[i].name +  ' Score: ' + PlayerList[i].score);
            var max_PlayerScoreDifference = 1000000;
            var min_index = 0
            index_PlayersPaired.push(i)
            PlayerScoreDifference[i] = []
            for (let j = i+1; j < PlayerList.length; j++) {
                PlayerScoreDifference[i][j] = Math.abs(PlayerList[i].score - PlayerList[j].score);
                alert('Score difference between Player ' + i + ' and Player ' + j + ' is ' + PlayerScoreDifference[i][j]);
                if  ( !(index_PlayersPaired.includes(j)) ) {
                    if (PlayerScoreDifference[i][j] < max_PlayerScoreDifference) {
                        max_PlayerScoreDifference = PlayerScoreDifference[i][j]
                        min_index = j
                    }
                }
            }
            //const min_index = PlayerScoreDifference[i].indexOf(Math.min(...PlayerScoreDifference[i]))
            index_PlayersPaired.push(min_index)
            alert(PlayerList[i].name + ' and ' +  PlayerList[min_index].name + ' are paired');
        }
    } 

    /*PlayerList.forEach((element_i, index_i) => {
        alert('Player: ' + index_i + ' Name: ' + element_i.name +  ' Score: ' + element_i.score);
        PlayerScoreDifference[index_i] = []

        PlayerList.forEach((element_j, index_j) => {
            PlayerScoreDifference[index_i][index_j] = element_i.score - element_j.score;
            alert('Score difference between Player ' + index_i + ' and Player ' + index_j + ' is ' + PlayerScoreDifference[index_i][index_j]);
        })
    }); */

    /* try {
        const response = await fetch(url+'leaderboard/allPlayers', {
            method: 'GET',
        });
        
        if (response.ok) {
            const playersByDivision = await response.json();
            playersByDivision.forEach((division, index) => {
            if (division.length > 0) {
                division.forEach(player => {
                    const playerDiv = document.createElement('div');
                    alert(${player.name})
                    // playerDiv.innerHTML = `
                        // Name: ${player.name}, Division: ${player.divisionNumber}, Score: ${player.score || 'N/A'}
                        // <div class="player-controls">
                            // <button onclick="updateScore('${player.name}', 2)">Win</button>
                            // <button onclick="updateScore('${player.name}', 1)">Draw</button>
                            // <button onclick="updateScore('${player.name}', 0)">Lose</button>
                            // <button onclick="deletePlayer('${player.name}')">Delete</button>
                        // </div>
                    //`;
                });
            } else {
                alert('Division length is 0. Failed to fetch players');
            }});
        } else {
            alert('Failed to fetch players');
        }
    } catch (error) {
        alert('Error: ' + error.message);
    }
    */

    return;
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
        const response = await fetch(url+'leaderboard/add', {
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
        const response = await fetch(url+'leaderboard/allPlayers', {
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
        const response = await fetch(url+'leaderboard/removeAll', {
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
        const response = await fetch(url+`/leaderboard/remove?name=${encodeURIComponent(playerName)}`, {
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
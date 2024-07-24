---
layout: none
permalink: /leaderboard
title: Del Norte Chess Club Leaderboard
---
{%- include chess_head.html -%}
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Leaderboard</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #005b96;
            color: #ffffff;
        }
        .leaderboard-container {
            width: 50%;
            margin: auto;
            padding-top: 20px;
        }
        .leaderboard-title {
            text-align: center;
            margin-top: 20px;
            margin-bottom: 10px;
            font-size: 24px;
            color: #60e085;
        }
        .leaderboard {
            width: 100%;
            margin-bottom: 20px;
            background-color: #0074cc;
            border-collapse: collapse;
        }
        .leaderboard th, .leaderboard td {
            border: 1px solid #ffffff;
            padding: 10px;
            text-align: left;
        }
        .leaderboard th {
            background-color: #005b96;
        }
        .dropdown {
            width: 100%;
            background-color: #0074cc;
            color: #ffffff;
            border: 1px solid #ffffff;
            padding: 10px;
            margin-bottom: 10px;
            text-align: center;
        }
        button {
            background-color: #60e085;
            color: #fff;
            padding: 5px 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="leaderboard-container">
        <select class="dropdown" onchange="showDivision(this.value)">
            <option value="all">All Divisions</option>
            <option value="1">Division 1</option>
            <option value="2">Division 2</option>
        </select>
        <div id="leaderboards"></div>
    </div>
<script>
    var deployed = "https://dnhs-chess-backend.onrender.com/";
    var local = "http://localhost:8085/"
    var url = deployed;
    document.addEventListener("DOMContentLoaded", () => {
        getAllPlayers();
    });

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

    function displayPlayers(playersByDivision) {
        const leaderboards = document.getElementById('leaderboards');
        leaderboards.innerHTML = '';
        for (const [division, players] of Object.entries(playersByDivision)) {
            const divisionNumber = parseInt(division, 10) + 1; // Increment division number
            
            // Sort players by score in descending order
            players.sort((a, b) => (b.score || 0) - (a.score || 0));
            
            const divisionTitle = document.createElement('div');
            divisionTitle.className = 'leaderboard-title';
            divisionTitle.textContent = `Division ${divisionNumber}`;
            leaderboards.appendChild(divisionTitle);
            
            const table = document.createElement('table');
            table.className = 'leaderboard';
            table.id = `division${divisionNumber}`;
            const headerRow = document.createElement('tr');
            headerRow.innerHTML = '<th>Rank</th><th>Name</th><th>Points</th>';
            table.appendChild(headerRow);
            
            players.forEach((player, index) => {
                const row = document.createElement('tr');
                row.innerHTML = `<td>${index + 1}</td><td>${player.name}</td><td>${player.score}</td>`;
                table.appendChild(row);
            });
            leaderboards.appendChild(table);
        }
        showDivision('all'); // Initially show all divisions
    }

    function showDivision(division) {
        const leaderboards = document.getElementById('leaderboards');
        const tables = leaderboards.getElementsByClassName('leaderboard');
        const titles = leaderboards.getElementsByClassName('leaderboard-title');
        for (let i = 0; i < tables.length; i++) {
            const isVisible = division === 'all' || tables[i].id === `division${division}`;
            tables[i].style.display = isVisible ? 'table' : 'none';
            titles[i].style.display = isVisible ? 'block' : 'none';
        }
    }
</script>
</body>
</html>
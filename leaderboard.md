---
layout: none
permalink: /leaderboard
title: Del Norte Chess Club Leaderboard
---
{%- include chess_head.html -%}
<style>
    p {
        text-align: center;
        background-color: #F6F6F2;
        color: #333;
    }
    ul {
        text-align: center;
        background-color: #F6F6F2;
        color: #333;
        font-size: 50px;
        font-family: Optima, sans-serif;
    }
    body {
        font-family: 'Arial', sans-serif;
        margin: 0;
        padding: 0;
        background-color: #F6F6F2;
        color: #333;
    }

    header {
        background-color: #F6F6F2;
        color: #F6F6F2;
        padding: 10px;
        text-align: center;
    }

    main {
        padding: 20px;
        background-color: #F6F6F2;
    }

    section {
        text-align: center;
        margin-top: 40px;
        background-color: ##D7B0AD;
    }

    h1.animated-title {
        font-family: Optima, sans-serif;
        color: #388087;
        font-size: 75px;
        background-color: ##D7B0AD;
        margin-top: 50px;
        animation: bounceIn 0.5s ease-out; /* Added animation for bouncing in */
    }

    h2 {
        font-family: Optima, sans-serif;
        color: #2f5154;
        font-size: 35px;
        background-color: #F6F6F2;
        text-align: center;
    }

    .search-title {
        font-family: Optima, sans-serif;
        color: #2f5154;
        font-size: 45px;
        background-color: ##D7B0AD;
        text-align: center;
        animation: moveUp 0.5s forwards; /* Added animation for moving up */
    }

    button {
        background-color: #60e085;
        color: #fff;
        padding: 5px 10px;
        border: none;
        border-radius: 5px;
        cursor: pointer;
    }

    footer {
        background-color: #F6F6F2;
        font-family: "Times New Roman", sans-serif;
        color: #388087;
        text-align: center;
        padding: 10px;
        position: fixed;
        bottom: 0;
        width: 100%;
    }

    .numbers {
        display: flex;
        justify-content: center;
        margin-top: 50px;
        font-family: "Times New Roman", sans-serif;
        color: #388087;
        font-size: 50px;
        background-color: #F6F6F2;
        margin-top: 10px;
        animation-duration: 1s;
        animation-fill-mode: forwards;
    }

    @keyframes moveUp {
        from { transform: translateY(0); }
        to { transform: translateY(-50px); } /* Adjust the distance to move up */
    }

    @keyframes bounceIn {
        from { opacity: 0; transform: scale(0.8); }
        to { opacity: 1; transform: scale(1); }
    }
</style>
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
        .leaderboard {
            width: 50%;
            margin: auto;
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
        }
    </style>
</head>
<body>
    <div class="leaderboard-container">
        <select class="dropdown" onchange="showDivision(this.value)" >
            <option value="division2" style="background-color:red">Division 2</option>
            <option value="division1" style="background-color:red">Division 1</option>
        </select>
        <table class="leaderboard" id="division2">
            <tr>
                <th>Rank</th>
                <th>Name</th>
                <th>Points</th>
            </tr>
            <tr><td>1</td><td>Magnus Carlsen</td><td>30</td></tr>
            <tr><td>2</td><td>Hikaru Nakamura</td><td>29</td></tr>
            <tr><td>3</td><td>Levy Rozman</td><td>28</td></tr>
            <tr><td>4</td><td>Nemo Zhou</td><td>27</td></tr>
            <tr><td>5</td><td>Alexandra Botez</td><td>20</td></tr>
            <tr><td>6</td><td>Ding Liren</td><td>18</td></tr>
            <tr><td>7</td><td>Bobby Fischer</td><td>15</td></tr>
            <tr><td>8</td><td>Hou Yi Fan</td><td>12</td></tr>
            <tr><td>9</td><td>Andrea Botez</td><td>11</td></tr>
            <tr><td>10</td><td>Pascal Basillion</td><td>10</td></tr>
            <tr><td>11</td><td>Jason Gao</td><td>9</td></tr>
            <tr><td>12</td><td>Nandan Vallamkondu</td><td>0</td></tr>
        </table>
        <table class="leaderboard" id="division1" style="display:none;">
            <tr>
                <th>Rank</th>
                <th>Name</th>
                <th>Points</th>
            </tr>
            <tr><td>1</td><td>Jschlatt</td><td>5</td></tr>
            <tr><td>2</td><td>Alex Xiao</td><td>4</td></tr>
            <tr><td>3</td><td>Lilian Wu</td><td>4</td></tr>
            <tr><td>4</td><td>Natalie Tao</td><td>4</td></tr>
            <tr><td>5</td><td>Jay He</td><td>4</td></tr>
            <tr><td>6</td><td>Alexander Randolph</td><td>3</td></tr>
            <tr><td>7</td><td>Logan Strother</td><td>3</td></tr>
            <tr><td>8</td><td>Sarah Hekmat</td><td>3</td></tr>
            <tr><td>9</td><td>Jadon Lee</td><td>3</td></tr>
            <tr><td>10</td><td>Alex Zhang</td><td>3</td></tr>
            <tr><td>11</td><td>Samarth Kalanke</td><td>3</td></tr>
            <tr><td>12</td><td>Preston Foster</td><td>0</td></tr>
        </table>
    </div>
    <script>
        function showDivision(division) {
            document.getElementById('division1').style.display = 'none';
            document.getElementById('division2').style.display = 'none';
            document.getElementById(division).style.display = 'table';
        }
    </script>
</body>
</html>

<style>
    /* Paste your CSS styles here */
    p {
        text-align: center;
        background-color: #F6F6F2;
        color: #333;
    }
    ul {
        text-align: center;
        background-color: #F6F6F2;
        color: #333;
        font-size: 50px;
        font-family: Optima, sans-serif;
    }
    body {
        font-family: 'Arial', sans-serif;
        margin: 0;
        padding: 0;
        background-color: #F6F6F2;
        color: #333;
    }
    header {
        background-color: #F6F6F2;
        color: #F6F6F2;
        padding: 10px;
        text-align: center;
    }
    main {
        padding: 20px;
        background-color: #F6F6F2;
    }
    section {
        text-align: center;
        margin-top: 40px;
        background-color: ##D7B0AD;
    }
    h1.animated-title {
        font-family: Optima, sans-serif;
        color: #388087;
        font-size: 75px;
        background-color: ##D7B0AD;
        margin-top: 50px;
        animation: bounceIn 0.5s ease-out; /* Added animation for bouncing in */
    }
    .numbers {
        display: flex;
        justify-content: center;
        margin-top: 50px;
        font-family: "Times New Roman", sans-serif;
        color: #388087;
        font-size: 50px;
        background-color: #F6F6F2;
        margin-top: 10px;
        animation-duration: 1s;
        animation-fill-mode: forwards;
    }
    @keyframes bounceIn {
        from { opacity: 0; transform: scale(0.8); }
        to { opacity: 1; transform: scale(1); }
    }
</style>

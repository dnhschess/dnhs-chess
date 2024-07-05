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

/* Make leaderboard */

{%- include chess_head.html -%}
<main>
    <section>
        <h1 class="animated-title">Leaderboard</h1>
        <div class="numbers">
            <ul>
                <li>1. Player A - 1500</li>
                <li>2. Player B - 1400</li>
                <li>3. Player C - 1300</li>
                <!-- Add more players as needed -->
            </ul>
        </div>
    </section>
</main>
<footer>
    <p>Del Norte Chess Club - Established 2020</p>
</footer>

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

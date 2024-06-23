---
layout: none
title: Del Norte Chess Club
search_exclude: true
---
{%- include chess_head.html -%}

<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DEL NORTE CHESS CLUB</title>
</head>

<body>
    <header>
        <p class="center1">
            <img src="{{site.baseurl}}/images/homepicture.png" width=750px/>
        </p>
        <h1 class="animated-title">DEL NORTE CHESS CLUB</h1>
    </header>
    <section id="search-section">
        <h1 class="search-title">Participate in various events</h1>
        <ul>Summer Camps</ul>
        <ul>Drop-In Tournaments</ul>
        <ul>Regional Tournaments</ul>
        <ul>Southern California Tournaments</ul>
        <!-- Add your job search form or any relevant content here -->
    </section>
    <!-- Add more sections as needed for additional content -->

</body>

</html>

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
        background-color: #F6F6F2;
    }

    h1.animated-title {
        font-family: Optima, sans-serif;
        color: #388087;
        font-size: 75px;
        background-color: #F6F6F2;
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
        background-color: #F6F6F2;
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

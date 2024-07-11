---
layout: none
search_exclude: true
permalink: /pastevents
---

<html>
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Your Title Here</title>

    <style>
        /* Resetting all margins and paddings to zero */
        * {
            margin: 0;
            padding: 0;
        }

        /* Setting a general background color */
        body {
            background-color: #FFD700; /* Yellowish color */
            font-family: "Montserrat", sans-serif;
            font-weight: 500;
            font-size: 20px;
            color: #333; /* Text color */
        }

        /* Styling the header */
        .nav_header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 30px 10%;
            background-color: #FFD700; /* Yellowish color */
            margin-bottom: 3ch;
        }

        /* Styling the logo */
        .logo {
            cursor: pointer;
        }

        /* Styling the navigation links */
        .nav_links {
            list-style: none;
        }

        .nav_links .nav_list {
            display: inline-block;
            padding: 5px 10px;
            border-radius: 10px; /* Slightly rounded edges */
            transition: background-color 0.3s ease 0s;
        }

        .nav_links .nav_list .nav_a {
            text-decoration: none;
            color: #333; /* Text color */
            font-size: 16px; /* Adjust the font size as needed */
        }

        .nav_links .nav_list:hover {
            background-color: #E0E0E0; /* Light gray background on hover */
        }

        .nav_links .nav_list .nav_a:hover {
            color: #555; /* Darker text color on hover */
        }

        /* Styling the navigation button */
        .nav_button {
            padding: 9px 25px;
            background-color: #FFD700; /* Yellowish color */
            border: none;
            cursor: pointer;
            transition: all 0.3s ease 0s;
            border-radius: 10px; /* Slightly rounded edges */
        }

        .nav_button:hover {
            background-color: #E0E0E0; /* Light gray background on hover */
        }
    </style>
</head>
<body>
    <header class="nav_header">
        <a href="{{ site.baseurl }}/">
            <img class="logo" src="{{ site.baseurl }}/images/chess_club_logo.png" alt="logo" width="100">
        </a>
        <nav>
            <ul class="nav_links">
                <li class="nav_list"><a class="nav_a" href="{{ site.baseurl }}/">Home</a></li>
                <li class="nav_list"><a class="nav_a" href="{{ site.baseurl }}/events">Events</a></li>
                <li class="nav_list"><a class="nav_a" href="{{ site.baseurl }}/pastevents">Past Events</a></li>
            </ul>
        </nav>
    </header>

    <!-- Your content here -->

    <p>
        <img src="{{ site.baseurl }}/images/bughousebrawl1.png" width="500px" />
        <img src="{{ site.baseurl }}/images/bughousebrawl2.png" width="500px" />
        <img src="{{ site.baseurl }}/images/bigbughousebrawl1.png" width="500px" />
    </p>

    <style>
        p {
            text-align: center;
            background-color: #FFFFFF; /* Set to white */
            color: #333;
        }

        li {
            text-align: center;
            background-color: #FFFFFF; /* Set to white */
            color: #2f5154;
        }

        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #FFFFFF; /* Set to white */
            color: #333;
        }

        header {
            background-color: #FFFFFF; /* Set to white */
            color: #333;
            padding: 10px;
            text-align: center;
        }

        main {
            padding: 10px;
            background-color: #FFFFFF; /* Set to white */
        }

        section {
            text-align: center;
            margin-top: 40px;
            background-color: #FFFFFF; /* Set to white */
        }

        h1.animated-title {
            font-family: Optima, sans-serif;
            color: #388087;
            font-size: 500px;
            background-color: #FFFFFF; /* Set to white */
            margin-top: 50px;
            animation: bounceIn 0.5s ease-out; /* Added animation for bouncing in */
        }

        h2 {
            font-family: Optima, sans-serif;
            color: #2f5154;
            font-size: 35px;
            background-color: #FFFFFF; /* Set to white */
            text-align: center;
        }

        .search-title {
            font-family: Optima, sans-serif;
            color: #2f5154;
            font-size: 45px;
            background-color: #FFFFFF; /* Set to white */
            text-align: center;
            animation: moveUp 0.5s forwards; /* Added animation for moving up */
        }

        a {
            background-color: #FFFFFF; /* Set the background color to white for URLs */
            color: #0000EE; /* Default color for links */
            text-decoration: none; /* Remove underline */
        }

        a:hover {
            background-color: #E0E0E0; /* Light gray background on hover */
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
            background-color: #FFFFFF; /* Set to white */
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
            background-color: #FFFFFF; /* Set to white */
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
</body>
</html>

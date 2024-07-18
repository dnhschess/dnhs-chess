---
layout: none
title: Del Norte Chess Club
search_exclude: true
---
{% include chess_head.html %}

<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Del Norte Chess Club</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
    <style>
        /* General Styles */
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f6f6f2;
            color: #333;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            text-align: center;
            padding: 20px 0;
        }

        h1 {
            font-family: 'Optima', sans-serif;
            font-size: 3rem;
            color: #388087;
            margin-top: 20px;
            animation: animate__fadeInDown 0.5s;
        }

        h2 {
            font-family: 'Optima', sans-serif;
            font-size: 2rem;
            color: #2f5154;
            text-align: center;
        }

        section {
            text-align: center;
            margin: 40px 0;
        }

        ul {
            list-style: none;
            padding: 0;
        }

        ul li {
            background-color: #fff;
            color: #388087;
            font-family: 'Optima', sans-serif;
            font-size: 1.5rem;
            padding: 15px 20px;
            border-radius: 10px;
            margin: 10px 0;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease-in-out;
        }

        ul li:hover {
            transform: scale(1.05);
        }

        footer {
            background-color: #f6f6f2;
            color: #388087;
            text-align: center;
            padding: 10px;
            position: fixed;
            bottom: 0;
            width: 100%;
            font-family: 'Times New Roman', sans-serif;
        }
    </style>
</head>

<body>
    <header>
    <img src="{{site.baseurl}}/images/homepicture.png" alt="Del Norte Chess Club" width="100%" style="margin-top: -60px;">
    <h1 class="animate__animated animate__fadeInDown">Del Norte Chess Club!</h1>
</header>
    <div class="container">
        <section>
            <h2>Participate in various events</h2>
            <ul>
                <li>Summer Camps</li>
                <li>Drop-In Tournaments</li>
                <li>Regional Tournaments</li>
                <li>Southern California Tournaments</li>
            </ul>
        </section>
        <section>
            <h2>Are you in Del Norte and want to join the Del Norte Chess Club?</h2>
            <ul>
                <li><a href="https://forms.gle/XBSdynUZsoNXvypM9">Fill out this form</a></li>
            </ul>
        </section>
    </div>
    <footer>
        <p>Join the Del Norte Discord!</p>
    </footer>

    <!-- Optional: Include animate.css for animations -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.js"></script>
</body>

</html>

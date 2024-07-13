---
layout: none
permalink: /signup
---
{%- include chess_head.html -%}
<style>
    body {
            background-color: #FFFF33; /* yellow background */
        }
        .CONTAINER {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .CARD {
            background-color: #f1f1f1; /* light grey background */
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            text-align: center;
        }
        h3 {
            font-size: 2em;
            margin-bottom: 20px;
            color: #333;
        }
        .input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        .signInButton {
            background-color: #FFA500; /* orange button */
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1em;
            width: 100%;
        }
        .signInButton:hover {
            background-color: #e69500; /* darker orange on hover */
        }
</style>
<html>
    <div class="CONTAINER">
        <div class="CARD">
            <h3>Sign Up Here</h3>
            <label>Enter your first name</label>
            <input class= "input" placeholder="Enter your first name" type="text" id="firstname">
            <input class="input" placeholder="Enter your last name" type="text" id="lastname">
            <input class="input" placeholder="Enter your email" type="email" id="email">
            <input class="input" placeholder="Enter your password" type = "password" id="pass">
            <button class="signInButton" onclick="Signup()">Login</button>
        </div>
    </div>
</html>
<script>
    function Signup() {
        let firstname = document.getElementById('firstname').value
        let  lastname = document.getElementById('lastname').value
        let  email = document.getElementById('email').value
        let  password = document.getElementById('pass').value
        var url = '' // add correct url
        payload = {
            firsname: firstname,
            lastname: lastname,
            email: email,
            password: password
        }
        json = JSON.stringify(payload)
        console.log(payload)
        const authOptions = {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: json,
            credentials: 'include'
        }
        fetch(url, authOptions)
            .then(response => {
                if (!response.ok) {
                    throw new Error(`HTTP error! Status: ${response.status}`);
                }
                return response.json();
            })
            .then(data => {
                console.log("Success");
            })
            .catch(error => {
                console.error('error', error);
            });
    }
</script>
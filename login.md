---
layout: none
permalink: /login
title: Del Norte Chess Club Login
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
            <h3>Login</h3>
            <input id="signInEmailInput" class="input" placeholder="Email">
            <input id="signInPasswordInput" class="input" placeholder="Password">
            <button class="signInButton" onclick="login_user()">Login</button>
        </div>
    </div>
</html>
<script>
function login_user() {
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");
    // STEP ONE: COLLECT USER INPUT
    var email = document.getElementById("signInEmailInput").value;
    var raw = JSON.stringify({
        "email": email,
        "password": document.getElementById("signInPasswordInput").value
        // For quick testing
        //"email": "toby@gmail.com",
        //"password": "123Toby!"
    });
    console.log(raw);
    var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        credentials: 'include',
        body: raw,
        redirect: 'follow'
    };
    // STEP TWO: SEND REQUEST TO BACKEND AND GET JWT COOKIE
    fetch("http://localhost:8085/authenticate", requestOptions)
    .then(response => {
        if (!response.ok) {
            const errorMsg = 'Login error: ' + response.status;
            console.log(errorMsg);
            switch (response.status) {
                case 401:
                    alert("Incorrect username or password");
                    break;
                case 403:
                    alert("Access forbidden. You do not have permission to access this resource.");
                    break;
                case 404:
                    alert("User not found. Please check your credentials.");
                    break;
                // Add more cases for other status codes as needed
                default:
                    alert("Login failed. Please try again later.");
            }
            return Promise.reject('Login failed');
        }
        return response.text();
    })
    .then(result => {
        console.log(result);
        //document.cookie = "email=" + encodeURIComponent(email) + "; path=/";
        localStorage.setItem('jwtToken', result.cookie);
        //window.location.replace("http://127.0.0.1:4200/dnhs-chess/");
        window.location.href = "https://dnhschess.github.io/dnhs-chess/";
    })
    .catch(error => console.error('Error during login:', error));
}
</script>

# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

Happy Coding! 💻✨


 1. HTML File (`index.html`)

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Animations and Local Storage</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1 id="welcomeMessage">Welcome to the Interactive Page!</h1>

    <button id="animateButton">Animate Me!</button>
    <button id="savePreferenceButton">Save Preference</button>

    <p id="infoText">Click the buttons to trigger animations or store preferences in local storage.</p>

    <script src="script.js"></script>
</body>
</html>


2. CSS File (`styles.css`)

body {
    font-family: Arial, sans-serif;
    margin: 20px;
    text-align: center;
}

button {
    margin: 10px;
    padding: 10px 20px;
    font-size: 18px;
    cursor: pointer;
    border: none;
    border-radius: 5px;
    background-color: #007BFF;
    color: white;
    transition: background-color 0.3s ease, transform 0.3s ease;
}

button:hover {
    background-color: #0056b3;
    transform: scale(1.1);
}

@keyframes bounce {
    0%, 20%, 50%, 80%, 100% {
        transform: translateY(0);
    }
    40% {
        transform: translateY(-20px);
    }
    60% {
        transform: translateY(-10px);
    }
}

.bouncing {
    animation: bounce 1s ease-in-out;
}




 3. JavaScript File (`script.js`)
// Get references to DOM elements
const animateButton = document.getElementById("animateButton");
const savePreferenceButton = document.getElementById("savePreferenceButton");
const welcomeMessage = document.getElementById("welcomeMessage");

// Function to trigger button animation
animateButton.addEventListener("click", function() {
    this.classList.add("bouncing");

    // Remove the animation class after it completes to allow retriggering
    setTimeout(() => {
        this.classList.remove("bouncing");
    }, 1000);
});

// Function to save user preferences in localStorage
savePreferenceButton.addEventListener("click", function() {
    const userPreference = "dark-theme"; // Example of saving a simple preference
    localStorage.setItem("themePreference", userPreference);

    // Feedback for the user
    alert("Your preference has been saved!");
});

// Retrieve and apply user preferences on page load
window.addEventListener("load", function() {
    const savedPreference = localStorage.getItem("themePreference");
    if (savedPreference) {
        // Example action based on preference
        welcomeMessage.textContent = `Welcome back! You prefer the ${savedPreference}.`;
        document.body.style.backgroundColor = savedPreference === "dark-theme" ? "#333" : "#FFF";
        document.body.style.color = savedPreference === "dark-theme" ? "#FFF" : "#000";
    }
});

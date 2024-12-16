<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Algebra Heist Terminal</title>
    <style>
        body {
            background-color: black;
            color: limegreen;
            font-family: "Courier New", Courier, monospace;
            padding: 20px;
        }
        .terminal {
            border: 2px solid limegreen;
            padding: 20px;
            max-width: 600px;
            margin: auto;
            text-align: left;
            position: relative;
        }
        .input-field {
            width: 90%;
            padding: 10px;
            margin-top: 10px;
            background-color: black;
            color: limegreen;
            border: 1px solid limegreen;
            font-family: "Courier New", Courier, monospace;
        }
        .button {
            padding: 10px;
            margin-top: 10px;
            background-color: limegreen;
            color: black;
            border: none;
            font-family: "Courier New", Courier, monospace;
            cursor: pointer;
        }
        .button:hover {
            background-color: darkgreen;
        }
        .output {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="terminal">

        <h1 align="center">CIAA</h1>
	<h4 align="center">Central Intelligence Algebra Agency</h4>
	<h2>CDOS-2 Hacking Terminal</h2>
        <p id="prompt">Evaluate the equation to proceed (Use the final code from the last mission): <strong>3x + 4y - 2p</strong></p>
        <input type="text" id="answer" class="input-field" placeholder="Enter your answer">
        <button class="button" onclick="checkAnswer()">Submit</button>
        <div class="output" id="output"></div>
    </div>

    <script>
        // Array of mini-mission problems and their solutions
        const problems = [
            { equation: "3x + 4y - 2p", solution: 81, clue: "Next expression: <strong>ACCESS 			DENIED</strong>" },
            { equation: "z^2 - 5p + q", solution: 155, clue: "Next equation: <strong>ACCESS DENIED</stong>" },
            { equation: "6(x + y) - 3(z - p)", solution: 120, clue: "<strong>ACCESS DENIED</stong>" },
{ equation: "q/p + z - x", solution: 7.5, clue: "<strong>Who needs a hint? You are almost there...keep hacking!</stong>"},
            { equation: "2z^2 - 3q + p", solution: 227, clue: "You've cracked the firewall! - <strong>Go to section 1b of CIAA document 1220-c for next steps from the Captain</strong>" }

        ];

        let currentProblemIndex = 0;

        function checkAnswer() {
            const userAnswer = parseInt(document.getElementById('answer').value);
            const output = document.getElementById('output');

            if (userAnswer === problems[currentProblemIndex].solution) {
                output.innerHTML = "Access Granted. " + problems[currentProblemIndex].clue;
                output.style.color = "limegreen";

                // Move to the next problem if available
                currentProblemIndex++;

                if (currentProblemIndex < problems.length) {
                    document.getElementById('prompt').innerHTML = "Evaluate the expression to proceed: <strong>" + problems[currentProblemIndex].equation + "</strong>";
                    document.getElementById('answer').value = "";
                } else {
                    document.getElementById('prompt').innerHTML = "Mission Complete! You've unlocked all the clues.";
                    document.getElementById('answer').style.display = "none";
                    document.querySelector('.button').style.display = "none";
                }
            } else {
                output.innerHTML = "Access Denied. Try Again.";
                output.style.color = "red";
            }
        }
    </script>
</body>
</html>

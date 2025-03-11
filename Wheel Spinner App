<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Conference Giveaway Wheel</title>
    <script src="https://cdn.jsdelivr.net/npm/@jaames/iro@5.5.1/dist/iro.min.js"></script>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; }
        #wheel { width: 300px; height: 300px; border-radius: 50%; border: 5px solid black; }
        #form-container { margin: 20px; }
    </style>
</head>
<body>
    <h1>Conference Giveaway Wheel</h1>
    <div id="form-container">
        <input type="text" id="name" placeholder="Enter Full Name" required>
        <input type="email" id="email" placeholder="Enter Email" required>
        <button onclick="addParticipant()">Enter</button>
    </div>
    <canvas id="wheel"></canvas>
    <button onclick="spinWheel()" id="spinButton" disabled>Spin the Wheel</button>
    <h2 id="winner"></h2>
    
    <script>
        let participants = [];
        let wheelSpinning = false;
        let lastWinner = null;
        let lastSpinTime = 0;

        function addParticipant() {
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            if (name && email) {
                participants.push({ name, email });
                document.getElementById('name').value = '';
                document.getElementById('email').value = '';
                updateWheel();
            }
        }
        
        function updateWheel() {
            document.getElementById('spinButton').disabled = participants.length < 3;
        }
        
        function spinWheel() {
            if (wheelSpinning || participants.length < 3) return;
            if (Date.now() - lastSpinTime < 3600000) { // 1 hour lock
                alert("A winner has already been chosen in the past hour. Please wait.");
                return;
            }
            
            wheelSpinning = true;
            let winnerIndex = Math.floor(Math.random() * participants.length);
            let winner = participants[winnerIndex];
            document.getElementById('winner').innerText = `Winner: ${winner.name}`;
            lastWinner = winner;
            lastSpinTime = Date.now();
            wheelSpinning = false;
        }
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Your Music Website</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
            background-color: black;
            color: white;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            border: 2px solid red;
            box-shadow: 0 0 10px red;
            padding: 20px;
        }
        .banner {
            width: 100%;
            margin-bottom: 20px;
        }
        .music-player {
            text-align: center;
            margin-top: 20px;
        }
        .track {
            margin: 20px;
            background-color: #1DB954;
            padding: 10px;
            border-radius: 5px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
        }
        .track audio {
            width: 100%;
        }
        .canvas-background {
            position: fixed;
            top: 0;
            left: 0;
            z-index: -1;
        }
        h1 {
            text-align: center;
            font-size: 2.5em;
        }
    </style>
</head>
<body>
    <canvas id="djCanvas" class="canvas-background"></canvas>

    <div class="container">
        <img src="https://i.imgur.com/0WXcUjd.jpeg" alt="Banner" class="banner">
        <img src="https://i.imgur.com/GNcZ5WF.jpeg" alt="Banner 2" class="banner">

        <h1>Welcome to Your Music Space</h1>

        <div class="music-player">
            <div class="track">
                <h2>Song Title</h2>
                <audio controls>
                    <source src="https://github.com/your-username/your-repo/raw/main/songs/song.mp3" type="audio/mpeg">
                    Your browser does not support the audio element.
                </audio>
            </div>
            <div class="track">
                <h2>Another Song</h2>
                <audio controls>
                    <source src="https://github.com/your-username/your-repo/raw/main/songs/another-song.mp3" type="audio/mpeg">
                    Your browser does not support the audio element.
                </audio>
            </div>
        </div>
    </div>

    <script>
        // Canvas DJ studio background effect
        var canvas = document.getElementById('djCanvas');
        var ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        function drawBackground() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            var gradient = ctx.createLinearGradient(0, 0, canvas.width, canvas.height);
            gradient.addColorStop(0, 'rgba(255,0,0,0.3)');
            gradient.addColorStop(1, 'rgba(0,0,0,0.3)');
            ctx.fillStyle = gradient;
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            // Visualize music vibes
            var bars = 50;
            var barWidth = (canvas.width / bars);
            var barHeight;
            for (var i = 0; i < bars; i++) {
                barHeight = Math.random() * canvas.height / 2;
                ctx.fillStyle = 'rgba(255,255,255,' + (i / bars) + ')';
                ctx.fillRect(i * barWidth, canvas.height - barHeight, barWidth - 2, barHeight);
            }
        }

        setInterval(drawBackground, 100);

        window.addEventListener('resize', function() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
    </script>
</body>
</html>

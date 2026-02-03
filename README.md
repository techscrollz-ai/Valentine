# <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For You ❤️</title>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.5.1/dist/confetti.browser.min.js"></script>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: linear-gradient(135deg, #ffafbd, #ffc3a0);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow: hidden;
        }
        .card {
            background: white;
            padding: 40px;
            border-radius: 30px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
            text-align: center;
            max-width: 400px;
            width: 90%;
        }
        h1 { color: #d63384; font-size: 2rem; margin-bottom: 30px; }
        .buttons { display: flex; justify-content: center; gap: 20px; position: relative; height: 60px; }
        button {
            padding: 12px 25px;
            font-size: 1.1rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
        }
        #yesBtn { background-color: #ff4d6d; color: white; box-shadow: 0 4px 15px rgba(255, 77, 109, 0.4); }
        #noBtn { background-color: #f8f9fa; color: #6c757d; position: absolute; left: 180px; }
        .celebration { display: none; }
    </style>
</head>
<body>

    <div class="card" id="quizCard">
        <div id="content">
            <h1>Will you be my Valentine? 🌹</h1>
            <div class="buttons">
                <button id="yesBtn">Yes</button>
                <button id="noBtn">No</button>
            </div>
        </div>
    </div>

    <script>
        const noBtn = document.getElementById('noBtn');
        const yesBtn = document.getElementById('yesBtn');
        const content = document.getElementById('content');

        const moveNo = () => {
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            noBtn.style.position = 'fixed';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
        };

        noBtn.addEventListener('mouseover', moveNo);
        noBtn.addEventListener('touchstart', (e) => { e.preventDefault(); moveNo(); });

        yesBtn.addEventListener('click', () => {
            confetti({ particleCount: 150, spread: 70, origin: { y: 0.6 } });
            content.innerHTML = `
                <h1 style="font-size: 3.5rem;">❤️</h1>
                <h2 style="color: #d63384;">Yay! See you soon!</h2>
                <p>Check your messages for the date details 😉</p>
            `;
            noBtn.style.display = 'none';
        });
    </script>
</body>
</html>

# hakuensai.github.io
<index.html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <link rel="icon" href="hakuensai.png" type="image/png">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>第69回柏苑祭までのカウントダウン</title>
    <style>
        :root {
            --bg-color: #0f172a;
            --card-bg: #1e293b;
            --text-main: #f8fafc;
            --text-sub: #94a3b8;
            --accent: #38bdf8;
        }

        body {
            margin: 0;
            padding: 0;
            font-family: 'Helvetica Neue', Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .container {
            text-align: center;
            padding: 2rem;
            max-width: 600px;
            width: 100%;
        }

         h1 {
            font-size: 1.8rem;
            margin-bottom: 2rem;
            color: var(--text-main);
            letter-spacing: 0.05em;
        }

        .target-date {
            color: var(--accent);
            font-weight: bold;
        }

        .countdown-container {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1rem;
            margin-bottom: 2rem;
        }

        .time-box {
            background-color: var(--card-bg);
            border-radius: 12px;
            padding: 1.5rem 0.5rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .number {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--accent);
            line-height: 1;
            margin-bottom: 0.5rem;
            font-variant-numeric: tabular-nums;
        }

        .label {
            font-size: 0.85rem;
            color: var(--text-sub);
            text-transform: uppercase;
            letter-spacing: 0.1em;
        }

        .message {
            font-size: 1.2rem;
            color: var(--text-sub);
            min-height: 1.5rem;
        }

        @media (max-width: 480px) {
            .countdown-container {
                gap: 0.5rem;
            }
            .number {
                font-size: 1.8rem;
            }
            .label {
                font-size: 0.75rem;
            }
        }
    </style>
</head>
<body>

    <div class="container">
        <h1><span class="target-date">第69回柏苑祭</span>までのカウントダウン</h1>
        
        <div class="countdown-container">
            <div class="time-box">
                <div class="number" id="days">00</div>
                <div class="label">日</div>
            </div>
            <div class="time-box">
                <div class="number" id="hours">00</div>
                <div class="label">時間</div>
            </div>
            <div class="time-box">
                <div class="number" id="minutes">00</div>
                <div class="label">分</div>
            </div>
            <div class="time-box">
                <div class="number" id="seconds">00</div>
                <div class="label">秒</div>
            </div>
        </div>

        <div class="message" id="message"></div>
    </div>

    <script>
        // 目標日時を 2027年9月25日 09:00:00 に変更
        const targetDate = new Date('2027-09-25T09:00:00').getTime();

        function updateCountdown() {
            const now = new Date().getTime();
            const difference = targetDate - now;

            const d = Math.floor(difference / (1000 * 60 * 60 * 24));
            const h = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const m = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60));
            const s = Math.floor((difference % (1000 * 60)) / 1000);

            document.getElementById('days').innerText = String(d).padStart(2, '0');
            document.getElementById('hours').innerText = String(h).padStart(2, '0');
            document.getElementById('minutes').innerText = String(m).padStart(2, '0');
            document.getElementById('seconds').innerText = String(s).padStart(2, '0');

            if (difference < 0) {
                clearInterval(timerInterval);
                document.getElementById('days').innerText = '00';
                document.getElementById('hours').innerText = '00';
                document.getElementById('minutes').innerText = '00';
                document.getElementById('seconds').innerText = '00';
                document.getElementById('message').innerText = 'ついに時間を迎えました！';
            }
        }

        const timerInterval = setInterval(updateCountdown, 1000);
        updateCountdown();
    </script>
</body>
</html>

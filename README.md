```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Happy Teacher's Day | Sir Randy Bello</title>

    <style>
        /* ================================
           PIXEL TEACHER'S DAY LETTER
           ================================ */

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --bg: #080808;
            --bg2: #111111;
            --card: #151515;
            --text: #ffffff;
            --muted: #a9a9a9;
            --pixel: #ffffff;
            --border: #333333;
            --shadow: rgba(255,255,255,0.08);
        }

        body.light {
            --bg: #eeeeee;
            --bg2: #ffffff;
            --card: #ffffff;
            --text: #111111;
            --muted: #555555;
            --pixel: #111111;
            --border: #cccccc;
            --shadow: rgba(0,0,0,0.15);
        }

        body {
            min-height: 100vh;
            font-family: "Courier New", monospace;
            background:
                linear-gradient(rgba(255,255,255,0.025) 1px, transparent 1px),
                linear-gradient(90deg, rgba(255,255,255,0.025) 1px, transparent 1px),
                var(--bg);
            background-size: 20px 20px;
            color: var(--text);
            overflow-x: hidden;
            transition: background 0.6s ease, color 0.6s ease;
        }

        /* ================================
           PIXEL BACKGROUND
           ================================ */

        .pixel {
            position: fixed;
            width: 8px;
            height: 8px;
            background: var(--pixel);
            opacity: 0.18;
            pointer-events: none;
            animation: floatPixel linear infinite;
        }

        .pixel:nth-child(1) {
            left: 10%;
            top: 20%;
            animation-duration: 8s;
        }

        .pixel:nth-child(2) {
            left: 80%;
            top: 30%;
            animation-duration: 11s;
        }

        .pixel:nth-child(3) {
            left: 25%;
            top: 70%;
            animation-duration: 9s;
        }

        .pixel:nth-child(4) {
            left: 70%;
            top: 80%;
            animation-duration: 13s;
        }

        .pixel:nth-child(5) {
            left: 50%;
            top: 10%;
            animation-duration: 10s;
        }

        @keyframes floatPixel {
            0% {
                transform: translateY(0) rotate(0deg);
                opacity: 0.1;
            }

            50% {
                transform: translateY(-50px) rotate(90deg);
                opacity: 0.4;
            }

            100% {
                transform: translateY(0) rotate(180deg);
                opacity: 0.1;
            }
        }

        /* ================================
           TOP BAR
           ================================ */

        .topbar {
            position: fixed;
            top: 20px;
            right: 25px;
            z-index: 100;
        }

        .theme-btn {
            border: 2px solid var(--border);
            background: var(--card);
            color: var(--text);
            padding: 10px 15px;
            font-family: inherit;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 4px 4px 0 var(--shadow);
            transition: 0.3s;
        }

        .theme-btn:hover {
            transform: translate(-2px, -2px);
            box-shadow: 7px 7px 0 var(--shadow);
        }

        /* ================================
           MAIN
           ================================ */

        .container {
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 40px 20px;
        }

        .content {
            width: 100%;
            max-width: 900px;
            text-align: center;
        }

        /* ================================
           TITLE
           ================================ */

        .pixel-title {
            font-size: clamp(28px, 6vw, 65px);
            font-weight: 900;
            letter-spacing: 5px;
            text-transform: uppercase;
            text-shadow:
                4px 4px 0 var(--pixel),
                -2px -2px 0 var(--bg);
            margin-bottom: 15px;
            animation: titleAppear 1s ease forwards;
        }

        .subtitle {
            color: var(--muted);
            font-size: 15px;
            letter-spacing: 2px;
            margin-bottom: 45px;
        }

        @keyframes titleAppear {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* ================================
           LETTER AREA
           ================================ */

        .letter-scene {
            perspective: 1200px;
        }

        .envelope {
            position: relative;
            width: min(90vw, 650px);
            height: 390px;
            margin: auto;
            cursor: pointer;
            transition: transform 0.5s ease;
        }

        .envelope:hover {
            transform: translateY(-8px);
        }

        .envelope-body {
            position: absolute;
            inset: 0;
            background: var(--card);
            border: 3px solid var(--border);
            box-shadow:
                10px 10px 0 var(--shadow),
                0 0 35px rgba(255,255,255,0.05);
            z-index: 2;
        }

        /* Pixel envelope lines */

        .envelope-body::before,
        .envelope-body::after {
            content: "";
            position: absolute;
            bottom: 0;
            width: 50%;
            height: 3px;
            background: var(--border);
        }

        .envelope-body::before {
            left: 0;
            transform-origin: left;
            transform: rotate(30deg);
        }

        .envelope-body::after {
            right: 0;
            transform-origin: right;
            transform: rotate(-30deg);
        }

        /* ================================
           FLAP
           ================================ */

        .flap {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 50%;
            background: var(--card);
            border: 3px solid var(--border);
            border-bottom: none;
            transform-origin: top;
            z-index: 5;
            transition:
                transform 1s cubic-bezier(.68,-0.55,.27,1.55),
                z-index 0.1s;
        }

        .flap::after {
            content: "✦";
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            font-size: 38px;
            color: var(--text);
            animation: blink 1.5s infinite;
        }

        @keyframes blink {
            0%, 100% {
                opacity: 1;
            }

            50% {
                opacity: 0.3;
            }
        }

        .envelope.open .flap {
            transform: rotateX(180deg);
            z-index: 1;
        }

        /* ================================
           LETTER
           ================================ */

        .letter {
            position: absolute;
            left: 5%;
            width: 90%;
            height: 90%;
            bottom: 2%;
            padding: 35px;
            background:
                linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
                var(--card);
            background-size: 15px 15px;
            border: 2px solid var(--border);
            z-index: 3;
            overflow-y: auto;

            transform: translateY(45%);
            opacity: 0;

            transition:
                transform 1.2s cubic-bezier(.2,.8,.2,1),
                opacity 0.8s ease;

            text-align: left;
        }

        .envelope.open .letter {
            transform: translateY(-12%);
            opacity: 1;
            z-index: 4;
        }

        .letter h2 {
            text-align: center;
            font-size: 25px;
            margin-bottom: 25px;
            letter-spacing: 2px;
        }

        .letter h2::before {
            content: "[ ";
        }

        .letter h2::after {
            content: " ]";
        }

        .letter p {
            color: var(--muted);
            line-height: 1.8;
            margin-bottom: 18px;
            font-size: 15px;
        }

        .letter .greeting {
            color: var(--text);
            font-weight: bold;
        }

        .signature {
            margin-top: 25px;
            text-align: right;
            font-weight: bold;
            color: var(--text);
        }

        /* ================================
           OPEN BUTTON
           ================================ */

        .open-text {
            margin-top: 40px;
            font-size: 13px;
            color: var(--muted);
            letter-spacing: 2px;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% {
                opacity: 0.5;
            }

            50% {
                opacity: 1;
            }
        }

        /* ================================
           FIREWORKS
           ================================ */

        .firework {
            position: fixed;
            width: 6px;
            height: 6px;
            background: var(--text);
            pointer-events: none;
            z-index: 200;
            animation: explode 1s ease-out forwards;
        }

        @keyframes explode {
            0% {
                transform: translate(0, 0);
                opacity: 1;
            }

            100% {
                transform:
                    translate(
                        calc((var(--x) - 50) * 4px),
                        calc((var(--y) - 50) * 4px)
                    );
                opacity: 0;
            }
        }

        /* ================================
           FOOTER
           ================================ */

        .footer {
            margin-top: 55px;
            font-size: 12px;
            color: var(--muted);
            letter-spacing: 1px;
        }

        /* ================================
           MOBILE
           ================================ */

        @media (max-width: 600px) {

            .envelope {
                height: 430px;
            }

            .letter {
                padding: 22px;
            }

            .letter p {
                font-size: 13px;
            }

            .pixel-title {
                letter-spacing: 2px;
            }
        }

    </style>
</head>

<body>

    <!-- Floating Pixel Decorations -->
    <div class="pixel"></div>
    <div class="pixel"></div>
    <div class="pixel"></div>
    <div class="pixel"></div>
    <div class="pixel"></div>

    <!-- Theme Switch -->
    <div class="topbar">
        <button class="theme-btn" id="themeButton">
            ☀ LIGHT MODE
        </button>
    </div>

    <main class="container">

        <section class="content">

            <h1 class="pixel-title">
                HAPPY TEACHER'S DAY
            </h1>

            <p class="subtitle">
                // A SPECIAL MESSAGE FOR MY WEB DEVELOPMENT INSTRUCTOR
            </p>

            <!-- Letter -->
            <div class="letter-scene">

                <div class="envelope" id="envelope">

                    <div class="envelope-body"></div>

                    <div class="flap"></div>

                    <article class="letter">

                        <h2>Dear Sir Randy Bello</h2>

                        <p class="greeting">
                            Happy Teacher's Day, Sir Randy!
                        </p>

                        <p>
                            I would like to take this opportunity to thank you
                            for being a great Web Development instructor.
                            Your lessons have helped us understand not only
                            how to create websites, but also how to think,
                            solve problems, and become better developers.
                        </p>

                        <p>
                            Thank you for your patience in teaching us HTML,
                            CSS, JavaScript, and the different concepts of
                            Web Development. Every activity and challenge
                            gives us an opportunity to learn something new
                            and improve our skills.
                        </p>

                        <p>
                            As students, we may sometimes make mistakes,
                            experience errors, or get confused with our code.
                            But those challenges are also part of learning.
                            Thank you for guiding us and encouraging us
                            to keep trying.
                        </p>

                        <p>
                            Your dedication as a teacher inspires us to
                            continue learning and developing our skills.
                            The knowledge and experience you share with us
                            will be useful not only in our studies but also
                            in our future careers.
                        </p>

                        <p>
                            Once again, thank you for your time, patience,
                            guidance, and dedication. We truly appreciate
                            everything you do for us.
                        </p>

                        <p class="signature">
                            Happy Teacher's Day, Sir Randy Bello!<br><br>
                            — Your Web Development Student
                        </p>

                    </article>

                </div>

            </div>

            <p class="open-text">
                ▶ CLICK THE ENVELOPE TO OPEN THE LETTER ◀
            </p>

            <footer class="footer">
                &lt;/&gt; Made with appreciation • Web Development
            </footer>

        </section>

    </main>

    <script>

        /* ================================
           OPEN / CLOSE LETTER
           ================================ */

        const envelope = document.getElementById("envelope");

        envelope.addEventListener("click", function () {

            this.classList.toggle("open");

            if (this.classList.contains("open")) {
                createFireworks();
            }

        });


        /* ================================
           DARK / LIGHT MODE
           ================================ */

        const themeButton = document.getElementById("themeButton");

        themeButton.addEventListener("click", function () {

            document.body.classList.toggle("light");

            if (document.body.classList.contains("light")) {
                this.innerHTML = "🌙 DARK MODE";
            } else {
                this.innerHTML = "☀ LIGHT MODE";
            }

        });


        /* ================================
           PIXEL FIREWORKS
           ================================ */

        function createFireworks() {

            for (let i = 0; i < 35; i++) {

                const firework = document.createElement("div");

                firework.classList.add("firework");

                const x = Math.random() * 100;
                const y = Math.random() * 100;

                firework.style.left = x + "%";
                firework.style.top = y + "%";

                firework.style.setProperty(
                    "--x",
                    Math.random() * 100
                );

                firework.style.setProperty(
                    "--y",
                    Math.random() * 100
                );

                document.body.appendChild(firework);

                setTimeout(() => {
                    firework.remove();
                }, 1000);

            }

        }


        /* ================================
           KEYBOARD INTERACTION
           ================================ */

        document.addEventListener("keydown", function(event) {

            if (event.key === "Enter" || event.key === " ") {
                envelope.classList.toggle("open");

                if (envelope.classList.contains("open")) {
                    createFireworks();
                }
            }

            if (event.key.toLowerCase() === "d") {
                document.body.classList.toggle("light");

                themeButton.innerHTML =
                    document.body.classList.contains("light")
                    ? "🌙 DARK MODE"
                    : "☀ LIGHT MODE";
            }

        });

    </script>

</body>
</html>
```

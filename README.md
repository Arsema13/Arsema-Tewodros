<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Arsema's GitHub Profile</title>
    <!-- Inter Font -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap" rel="stylesheet">
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background: #0d1117;
            background-size: 400% 400%;
            overflow: hidden;
        }

        /* Particle Animation */
        .animated-background-particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
            background: linear-gradient(-45deg, #1f2937, #111827, #1f2937, #0d1117);
            background-size: 400% 400%;
            animation: gradient-animation 15s ease infinite;
        }

        .animated-background-particles::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 10% 10%, rgba(236, 72, 153, 0.2), transparent 25%),
                        radial-gradient(circle at 90% 90%, rgba(139, 92, 246, 0.2), transparent 25%),
                        radial-gradient(circle at 70% 30%, rgba(236, 72, 153, 0.2), transparent 25%),
                        radial-gradient(circle at 30% 70%, rgba(139, 92, 246, 0.2), transparent 25%);
            background-size: 200% 200%;
            animation: particle-animation 25s ease infinite;
        }

        @keyframes gradient-animation {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes particle-animation {
            0% { background-position: 0% 0%; }
            50% { background-position: 100% 100%; }
            100% { background-position: 0% 0%; }
        }

        .typing-cursor {
            display: inline-block;
            width: 4px;
            height: 1.2em;
            background-color: #f87171;
            animation: blink-caret 0.75s step-end infinite;
            vertical-align: middle;
            margin-left: 2px;
        }
        @keyframes blink-caret {
            from, to { opacity: 0; }
            50% { opacity: 1; }
        }
        .stats-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 1.5rem;
            margin-top: 2rem;
        }
        .stat-card {
            background-color: #1f2937;
            border-radius: 1.5rem;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
            padding: 1rem;
            max-width: 100%;
            overflow: hidden;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .stat-card:hover {
            transform: translateY(-5px) scale(1.02);
            box-shadow: 0 0 25px rgba(236, 72, 153, 0.5), 0 0 10px rgba(139, 92, 246, 0.5);
        }
    </style>
</head>
<body class="bg-gray-900 flex flex-col items-center justify-center py-12 px-4">
    <div class="animated-background-particles"></div>

    <!-- Profile Header Section -->
    <div class="max-w-4xl w-full p-8 md:p-12 bg-gray-800 text-white rounded-3xl shadow-2xl transform transition-transform duration-500 hover:scale-105">
        <div class="flex flex-col md:flex-row items-center justify-center space-y-6 md:space-y-0 md:space-x-12 text-center md:text-left">
            <!-- Profile Placeholder -->
            <div class="flex-shrink-0">
                <div class="w-32 h-32 md:w-48 md:h-48 rounded-full bg-gradient-to-br from-pink-500 to-purple-600 flex items-center justify-center overflow-hidden border-4 border-gray-700">
                    <!-- The circular vibrant background remains -->
                </div>
            </div>
            <!-- Text Content -->
            <div class="space-y-4">
                <h1 class="text-4xl md:text-5xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-pink-500 to-purple-600">
                    Hi, my name is Arsema Tewodros
                </h1>
                <p class="text-2xl md:text-3xl font-light text-gray-300">
                    I'm a <span id="typed-text" class="font-semibold text-white"></span><span class="typing-cursor"></span>
                </p>
            </div>
        </div>
    </div>

    <!-- GitHub Stats Section -->
    <div class="stats-container w-full max-w-4xl">
        <!-- Main Stats Card -->
        <img src="https://github-readme-stats.vercel.app/api?username=Arsema13&show_icons=true&theme=dark&hide_border=true&bg_color=1f2937&count_private=true" alt="Arsema's GitHub Stats" class="stat-card" />
        <!-- Streak Stats Card -->
        <img src="https://github-readme-streak-stats.herokuapp.com?user=Arsema13&theme=dark&hide_border=true&background=1f2937&ring=bf40bf&side_most_ring=bf40bf&currStreakNum=bf40bf&fire=bf40bf&stroke=bf40bf" alt="Arsema's GitHub Streak" class="stat-card" />
        <!-- Top Languages Card -->
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Arsema13&layout=compact&theme=dark&hide_border=true&bg_color=1f2937&title_color=bf40bf" alt="Arsema's Top Languages" class="stat-card" />
    </div>

    <script>
        document.addEventListener("DOMContentLoaded", function() {
            const typedTextElement = document.getElementById('typed-text');
            const words = ["Mobile App Developer.", "Web Developer."];
            let wordIndex = 0;
            let charIndex = 0;
            let isDeleting = false;

            const type = () => {
                const currentWord = words[wordIndex];
                if (isDeleting) {
                    typedTextElement.textContent = currentWord.substring(0, charIndex - 1);
                    charIndex--;
                } else {
                    typedTextElement.textContent = currentWord.substring(0, charIndex + 1);
                    charIndex++;
                }

                if (!isDeleting && charIndex === currentWord.length) {
                    isDeleting = true;
                    setTimeout(type, 1500); // Pause before deleting
                } else if (isDeleting && charIndex === 0) {
                    isDeleting = false;
                    wordIndex = (wordIndex + 1) % words.length;
                    setTimeout(type, 500); // Pause before typing next word
                } else {
                    const typingSpeed = isDeleting ? 75 : 150;
                    setTimeout(type, typingSpeed);
                }
            };

            type();
        });
    </script>
</body>
</html>

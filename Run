<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Predictive Suckiness Scale</title>
    <style>
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #fff;
            color: #333;
            text-align: center;
        }
        header {
            background-color: #f8f8f8;
            border-bottom: 1px solid #e0e0e0;
            padding: 1.5rem 0;
        }
        header h1 {
            font-size: 2rem;
            margin: 0;
            color: #111;
        }
        header p {
            font-size: 1rem;
            color: #555;
        }
        main {
            padding: 2rem 1rem;
        }
        form {
            max-width: 600px;
            margin: 1rem auto;
            background: #f8f8f8;
            padding: 2rem;
            border-radius: 12px;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
        }
        .question {
            margin-bottom: 2rem;
        }
        label {
            display: block;
            margin-bottom: 0.5rem;
            font-size: 1.1rem;
            color: #111;
        }
        input[type="radio"] {
            margin-right: 0.5rem;
        }
        button {
            background-color: #007aff;
            color: white;
            border: none;
            padding: 0.75rem 1.5rem;
            font-size: 1rem;
            border-radius: 24px;
            cursor: pointer;
            box-shadow: 0 4px 6px rgba(0, 122, 255, 0.4);
            transition: background-color 0.3s ease;
        }
        button:hover {
            background-color: #005bb5;
        }
        .results {
            margin-top: 2rem;
            padding: 2rem;
            background: #f8f8f8;
            border-radius: 12px;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
            font-size: 1.2rem;
            color: #111;
        }
        ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }
    </style>
</head>
<body>
    <header>
        <h1>Predictive Suckiness Scale</h1>
        <p>Check your mindset and take steps to "Be Less Sucky"</p>
    </header>
    <main>
        <section id="intro">
            <h2>Welcome to the Predictive Suckiness Scale</h2>
            <p>We all have moments where emotions or stress lead us to say or do things we regret. The Predictive Suckiness Scale (PSS) helps you understand your current state and take action before things escalate.</p>
            <p><strong>Instructions:</strong> Answer one question at a time based on how you feel right now. Use this scale:</p>
            <ul>
                <li>1 = Strongly Disagree</li>
                <li>2 = Disagree</li>
                <li>3 = Neutral</li>
                <li>4 = Agree</li>
                <li>5 = Strongly Agree</li>
            </ul>
            <button onclick="startPSS()">Start the Scale</button>
        </section>

        <section id="pss" style="display:none;">
            <form id="suckinessForm">
                <div id="question-container" class="question">
                    <!-- Questions will load here dynamically -->
                </div>
                <button type="button" id="nextButton" onclick="nextQuestion()" style="display:none;">Next</button>
                <button type="button" id="submitButton" onclick="calculateScore()" style="display:none;">Submit</button>
            </form>

            <div id="results" class="results" style="display:none;"></div>
        </section>
    </main>

    <script>
        const questions = [
            "I feel overwhelmed by everything I have to do today.",
            "I feel close to losing my temper or snapping.",
            "Little things are getting under my skin more than usual.",
            "I don’t feel like I have the energy to deal with problems or challenges.",
            "I feel physically tense (e.g., tight muscles, shallow breathing).",
            "I’m thinking a lot about past mistakes or failures.",
            "I’m struggling to be patient with people around me.",
            "I’m finding it hard to focus on what I’m doing."
        ];

        let currentQuestionIndex = 0;
        let totalScore = 0;

        function startPSS() {
            document.getElementById('intro').style.display = 'none';
            document.getElementById('pss').style.display = 'block';
            loadQuestion();
        }

        function loadQuestion() {
            const questionContainer = document.getElementById('question-container');
            questionContainer.innerHTML = `
                <label>${currentQuestionIndex + 1}. ${questions[currentQuestionIndex]}</label>
                <input type="radio" name="answer" value="1" required> Strongly Disagree
                <input type="radio" name="answer" value="2"> Disagree
                <input type="radio" name="answer" value="3"> Neutral
                <input type="radio" name="answer" value="4"> Agree
                <input type="radio" name="answer" value="5"> Strongly Agree
            `;

            document.getElementById('nextButton').style.display = currentQuestionIndex < questions.length - 1 ? 'inline-block' : 'none';
            document.getElementById('submitButton').style.display = currentQuestionIndex === questions.length - 1 ? 'inline-block' : 'none';
        }

        function nextQuestion() {
            const selectedAnswer = document.querySelector('input[name="answer"]:checked');
            if (!selectedAnswer) {
                alert('Please select an answer before proceeding.');
                return;
            }

            totalScore += parseInt(selectedAnswer.value);
            currentQuestionIndex++;

            if (currentQuestionIndex < questions.length) {
                loadQuestion();
            }
        }

        function calculateScore() {
            const selectedAnswer = document.querySelector('input[name="answer"]:checked');
            if (!selectedAnswer) {
                alert('Please select an answer before submitting.');
                return;
            }

            totalScore += parseInt(selectedAnswer.value);

            const resultsDiv = document.getElementById('results');
            let feedback = "";

            if (totalScore <= 16) {
                feedback = "<strong>Score: " + totalScore + "</strong><br>You’re in control. Your emotional and mental state is balanced. You’re in a good place to interact with others and make thoughtful decisions.";
            } else if (totalScore <= 24) {
                feedback = "<strong>Score: " + totalScore + "</strong><br>Proceed with caution. You’re feeling some strain. This is a good time to slow down, take a break, and manage your stress levels before reacting to others.";
            } else if (totalScore <= 32) {
                feedback = "<strong>Score: " + totalScore + "</strong><br>High risk. You’re under significant mental or emotional strain. Your responses suggest you may be close to reacting impulsively or regrettably. Step back, practice mindfulness, or engage in self-care to regain control.";
            } else {
                feedback = "<strong>Score: " + totalScore + "</strong><br>Critical. Your emotional and cognitive load is very high. You’re in a reactive state, and it’s likely that you’ll say or do something you regret. Take immediate action to reduce stress and avoid high-stakes interactions until you’ve had a chance to reset.";
            }

            resultsDiv.innerHTML = `<h2>Your Results</h2><p>${feedback}</p>`;
            resultsDiv.style.display = "block";
            document.getElementById('pss').style.display = 'none';
        }
    </script>
</body>
</html>

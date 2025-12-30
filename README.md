<!DOCTYPE html>
<html lang="km">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ហ្គេមសំណួរសង្គម</title>
    <style>
        body {
            font-family: "Khmer OS", sans-serif;
            background-color: #f0f8ff;
            text-align: center;
            padding: 20px;
        }
        #quiz-container {
            background-color: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.2);
            max-width: 600px;
            margin: auto;
        }
        .question {
            font-size: 20px;
            margin-bottom: 20px;
        }
        .answer-btn {
            display: block;
            margin: 10px auto;
            padding: 10px 20px;
            font-size: 18px;
            cursor: pointer;
            border-radius: 5px;
            border: none;
            background-color: #4CAF50;
            color: white;
            transition: background-color 0.3s;
        }
        .answer-btn:hover {
            background-color: #45a049;
        }
        #score {
            font-size: 22px;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div id="quiz-container">
        <div id="question" class="question"></div>
        <div id="answers"></div>
        <div id="score"></div>
    </div>

    <script>
        const quizData = [
            {
                question: "តើប្រទេសកម្ពុជាដែលមានប្រជាជនច្រើនបំផុតនៅទីក្រុងណា?",
                answers: ["ភ្នំពេញ", "សៀមរាប", "បាត់ដំបង", "កំពង់ឆ្នាំង"],
                correct: "ភ្នំពេញ"
            },
            {
                question: "តើប្រទេសកម្ពុជាមានច្បាប់ស្ដីពីការការពារសិទ្ធិមនុស្សទេ?",
                answers: ["មាន", "គ្មាន"],
                correct: "មាន"
            },
            {
                question: "តើអង្គការសហប្រជាជាតិកើតឡើងនៅឆ្នាំណា?",
                answers: ["1945", "1948", "1950", "1949"],
                correct: "1945"
            }
        ];

        let currentQuestion = 0;
        let score = 0;

        function showQuestion() {
            const questionEl = document.getElementById('question');
            const answersEl = document.getElementById('answers');
            const scoreEl = document.getElementById('score');

            if(currentQuestion < quizData.length){
                questionEl.textContent = quizData[currentQuestion].question;
                answersEl.innerHTML = '';

                quizData[currentQuestion].answers.forEach(answer => {
                    const button = document.createElement('button');
                    button.textContent = answer;
                    button.classList.add('answer-btn');
                    button.addEventListener('click', () => checkAnswer(answer));
                    answersEl.appendChild(button);
                });

                scoreEl.textContent = `ពិន្ទុ: ${score}`;
            } else {
                questionEl.textContent = "ហ្គេមបានបញ្ចប់!";
                answersEl.innerHTML = '';
                scoreEl.textContent = `សរុបពិន្ទុ: ${score} / ${quizData.length}`;
            }
        }

        function checkAnswer(answer){
            if(answer === quizData[currentQuestion].correct){
                score++;
                alert("ចម្លើយត្រឹមត្រូវ!");
            } else {
                alert(`ចម្លើយខុស! ចម្លើយត្រឹមត្រូវ: ${quizData[currentQuestion].correct}`);
            }
            currentQuestion++;
            showQuestion();
        }

        showQuestion();
    </script>
</body>
</html>

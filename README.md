<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fill in the Blanks Game</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #6a93cb 0%, #a4bfef 100%);
            min-height: 100vh;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .container {
            max-width: 800px;
            width: 100%;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
            overflow: hidden;
        }
        
        .header {
            background: linear-gradient(135deg, #4a6fa5, #6a93cb);
            color: white;
            padding: 25px;
            text-align: center;
        }
        
        .header h1 {
            font-size: 2.2em;
            margin-bottom: 10px;
        }
        
        .header p {
            font-size: 1.1em;
            opacity: 0.9;
        }
        
        .word-bank {
            background: #f5f7fa;
            padding: 20px;
            border-bottom: 2px solid #ddd;
        }
        
        .word-bank h3 {
            color: #4a6fa5;
            margin-bottom: 15px;
            text-align: center;
        }
        
        .word-options {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
        }
        
        .word-option {
            background: #4a6fa5;
            color: white;
            padding: 8px 15px;
            border-radius: 20px;
            font-weight: bold;
        }
        
        .questions-container {
            padding: 25px;
        }
        
        .question {
            margin-bottom: 25px;
            padding: 20px;
            border-radius: 10px;
            background: #f8f9fa;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
        }
        
        .question h3 {
            color: #4a6fa5;
            margin-bottom: 15px;
            padding-bottom: 8px;
            border-bottom: 2px solid #e9ecef;
        }
        
        .fill-blank {
            background: #fff;
            border: 2px solid #ddd;
            border-radius: 5px;
            padding: 6px 10px;
            font-size: 16px;
            margin: 0 5px;
            min-width: 120px;
            transition: border-color 0.3s ease;
        }
        
        .fill-blank:focus {
            outline: none;
            border-color: #4a6fa5;
        }
        
        .fill-blank.correct {
            border-color: #4CAF50;
            background: #e8f5e8;
        }
        
        .fill-blank.incorrect {
            border-color: #f44336;
            background: #ffeaea;
        }
        
        .feedback {
            margin-top: 15px;
            padding: 12px;
            border-radius: 8px;
            font-weight: bold;
            display: none;
        }
        
        .feedback.correct {
            background: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }
        
        .feedback.incorrect {
            background: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }
        
        .buttons {
            display: flex;
            justify-content: center;
            gap: 15px;
            padding: 20px;
        }
        
        .btn {
            padding: 12px 25px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: all 0.3s ease;
        }
        
        .check-btn {
            background: #4a6fa5;
            color: white;
        }
        
        .check-btn:hover {
            background: #3c5a84;
            transform: translateY(-2px);
        }
        
        .reset-btn {
            background: #e9ecef;
            color: #495057;
        }
        
        .reset-btn:hover {
            background: #dee2e6;
            transform: translateY(-2px);
        }
        
        .score-container {
            text-align: center;
            padding: 15px;
            font-size: 1.2em;
            font-weight: bold;
            color: #4a6fa5;
            border-top: 2px solid #e9ecef;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>Fill in the Blanks Game</h1>
            <p>Complete the sentences with the correct words from the word bank</p>
        </div>
        
        <div class="word-bank">
            <h3>Word Bank</h3>
            <div class="word-options">
                <span class="word-option">enable</span>
                <span class="word-option">come up with</span>
                <span class="word-option">tournament</span>
                <span class="word-option">a walk in the park</span>
                <span class="word-option">unlikely</span>
            </div>
        </div>
        
        <div class="questions-container">
            <div class="question">
                <h3>Question 1</h3>
                <p>This new software will <input type="text" class="fill-blank" data-answer="enable" placeholder="enter answer"> teachers to track student progress more effectively.</p>
                <div class="feedback" id="feedback-1"></div>
            </div>
            
            <div class="question">
                <h3>Question 2</h3>
                <p>These hearing aids <input type="text" class="fill-blank" data-answer="enable" placeholder="enter answer"> people with hearing impairments to participate in conversations more easily.</p>
                <div class="feedback" id="feedback-2"></div>
            </div>
            
            <div class="question">
                <h3>Question 3</h3>
                <p>The marketing team needs to <input type="text" class="fill-blank" data-answer="come up with" placeholder="enter answer"> fresh ideas for the upcoming campaign by tomorrow.</p>
                <div class="feedback" id="feedback-3"></div>
            </div>
            
            <div class="question">
                <h3>Question 4</h3>
                <p>The annual golf <input type="text" class="fill-blank" data-answer="tournament" placeholder="enter answer"> at the country club attracts professional players from around the world.</p>
                <div class="feedback" id="feedback-4"></div>
            </div>
            
            <div class="question">
                <h3>Question 5</h3>
                <p>For an experienced climber like Alex, scaling this small hill is <input type="text" class="fill-blank" data-answer="a walk in the park" placeholder="enter answer"> compared to the mountains he usually climbs.</p>
                <div class="feedback" id="feedback-5"></div>
            </div>
            
            <div class="question">
                <h3>Question 6</h3>
                <p>It's <input type="text" class="fill-blank" data-answer="unlikely" placeholder="enter answer"> that the package will arrive today since it only shipped yesterday.</p>
                <div class="feedback" id="feedback-6"></div>
            </div>
            
            <div class="question">
                <h3>Question 7</h3>
                <p>Given his fear of heights, it's <input type="text" class="fill-blank" data-answer="unlikely" placeholder="enter answer"> that Mark will ever try skydiving.</p>
                <div class="feedback" id="feedback-7"></div>
            </div>
            
            <div class="question">
                <h3>Question 8</h3>
                <p>The video game <input type="text" class="fill-blank" data-answer="tournament" placeholder="enter answer"> had a prize pool of over $100,000 for the winning team.</p>
                <div class="feedback" id="feedback-8"></div>
            </div>
            
            <div class="question">
                <h3>Question 9</h3>
                <p>Can you <input type="text" class="fill-blank" data-answer="come up with" placeholder="enter answer"> a better excuse for being late? That one just isn't believable.</p>
                <div class="feedback" id="feedback-9"></div>
            </div>
            
            <div class="question">
                <h3>Question 10</h3>
                <p>After solving complex calculus problems, these simple arithmetic questions are <input type="text" class="fill-blank" data-answer="a walk in the park" placeholder="enter answer"> for the math prodigy.</p>
                <div class="feedback" id="feedback-10"></div>
            </div>
        </div>
        
        <div class="buttons">
            <button class="btn check-btn" onclick="checkAnswers()">Check Answers</button>
            <button class="btn reset-btn" onclick="resetGame()">Reset Game</button>
        </div>
        
        <div class="score-container">
            Score: <span id="score">0</span>/10
        </div>
    </div>

    <script>
        function checkAnswers() {
            const blanks = document.querySelectorAll('.fill-blank');
            let score = 0;
            
            blanks.forEach((blank, index) => {
                const userAnswer = blank.value.toLowerCase().trim();
                const correctAnswer = blank.dataset.answer.toLowerCase();
                const feedback = document.getElementById(`feedback-${index+1}`);
                
                if (userAnswer === correctAnswer) {
                    blank.classList.remove('incorrect');
                    blank.classList.add('correct');
                    feedback.textContent = '✓ Correct!';
                    feedback.classList.add('correct');
                    feedback.classList.remove('incorrect');
                    feedback.style.display = 'block';
                    score++;
                } else {
                    blank.classList.remove('correct');
                    blank.classList.add('incorrect');
                    feedback.textContent = `✗ Incorrect. The correct answer is: "${blank.dataset.answer}"`;
                    feedback.classList.add('incorrect');
                    feedback.classList.remove('correct');
                    feedback.style.display = 'block';
                }
            });
            
            document.getElementById('score').textContent = score;
        }
        
        function resetGame() {
            const blanks = document.querySelectorAll('.fill-blank');
            const feedbacks = document.querySelectorAll('.feedback');
            
            blanks.forEach(blank => {
                blank.value = '';
                blank.classList.remove('correct', 'incorrect');
            });
            
            feedbacks.forEach(feedback => {
                feedback.textContent = '';
                feedback.classList.remove('correct', 'incorrect');
                feedback.style.display = 'none';
            });
            
            document.getElementById('score').textContent = '0';
        }
    </script>
</body>
</html>

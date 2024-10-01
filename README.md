git clone https://github.com/username/nielmarjosh.github.io
<!DOCTYPE html>
<html>
<head>
    <title>Grade Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .container {
            width: 50%;
            margin: 40px auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        label {
            display: block;
            margin-bottom: 10px;
        }
        input[type="number"] {
            width: 100%;
            height: 30px;
            margin-bottom: 20px;
            padding: 10px;
            border: 1px solid #ccc;
        }
        button[type="submit"] {
            width: 100%;
            height: 30px;
            background-color: #4CAF50;
            color: #fff;
            padding: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button[type="submit"]:hover {
            background-color: #3e8e41;
        }
        .result {
            margin-top: 20px;
            font-size: 18px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Grade Calculator</h2>
        <form id="grade-form">
            <label for="prelim-grade">Prelim Grade:</label>
            <input type="number" id="prelim-grade" name="prelim-grade" required>

            <label for="midterm-grade">Midterm Grade:</label>
            <input type="number" id="midterm-grade" name="midterm-grade" required>

            <label for="final-grade">Final Grade:</label>
            <input type="number" id="final-grade" name="final-grade" required>

            <button type="submit">Calculate Grade</button>
        </form>
        <div class="result" id="result"></div>
    </div>

    <script>
        const form = document.getElementById('grade-form');
        form.addEventListener('submit', calculateGrade);

        function calculateGrade(event) {
            event.preventDefault();
            const prelimGrade = parseFloat(document.getElementById('prelim-grade').value);
            const midtermGrade = parseFloat(document.getElementById('midterm-grade').value);
            const finalGrade = parseFloat(document.getElementById('final-grade').value);

            const prelimWeighted = 0.2 * prelimGrade;
            const midtermWeighted = 0.3 * midtermGrade;
            const finalWeighted = 0.5 * finalGrade;

            const overallGrade = prelimWeighted + midtermWeighted + finalWeighted;

            const resultDiv = document.getElementById('result');
            if (overallGrade < 75) {
                resultDiv.innerText = Failed. The passing grade is 75.;
            } else {
                resultDiv.innerText = Congratulations, you are passed! Your overall grade is ${overallGrade.toFixed(2)}.;
            }
        }
    </script>
</body>
</html>

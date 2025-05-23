<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EMI Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 255, 0, 0.7);
            width: 90%;
            max-width: 400px;
            transition: box-shadow 0.3s ease-in-out;
        }
        .container:hover {
            box-shadow: 0 0 25px rgb(74, 14, 41);
        }
        input, button {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background: #011807;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background: #4108c8;
        }
        #result {
            font-weight: bold;
            text-align: center;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>EMI Calculator</h2>
        <label for="loanAmount">Loan Amount:</label>
        <input type="number" id="loanAmount" placeholder="Enter loan amount">
        
        <label for="interestRate">Annual Interest Rate (%):</label>
        <input type="number" id="interestRate" placeholder="Enter interest rate">
        
        <label for="loanTenure">Loan Tenure (months):</label>
        <input type="number" id="loanTenure" placeholder="Enter tenure in months">
        
        <button onclick="calculateEMI()">Calculate EMI</button>
        
        <p id="result"></p>
    </div>

    <script>
        function calculateEMI() {
            let loanAmount = document.getElementById("loanAmount").value;
            let interestRate = document.getElementById("interestRate").value;
            let loanTenure = document.getElementById("loanTenure").value;
            
            if (loanAmount == "" || interestRate == "" || loanTenure == "") {
                document.getElementById("result").innerText = "Please enter all values";
                return;
            }
            
            let monthlyRate = (interestRate / 100) / 12;
            let emi = (loanAmount * monthlyRate * Math.pow(1 + monthlyRate, loanTenure)) / 
                      (Math.pow(1 + monthlyRate, loanTenure) - 1);
            emi = emi.toFixed(2);
            
            document.getElementById("result").innerText = `Your EMI: ₹${emi}`;
        }
    </script>
</body>
</html>

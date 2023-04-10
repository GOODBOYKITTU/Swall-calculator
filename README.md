<!DOCTYPE html>
<html>
  <head>
    <title>Compound Interest Calculator</title>
  </head>
  <body>
    <h1>Compound Interest Calculator</h1>
    <form>
      <label for="initial-amount">Initial amount:</label>
      <input type="number" id="initial-amount" name="initial-amount"><br>

      <label for="daily-interest-rate">Daily interest rate:</label>
      <input type="number" id="daily-interest-rate" name="daily-interest-rate" value="0.8" readonly><br>

      <label for="num-days">Number of days:</label>
      <input type="number" id="num-days" name="num-days"><br>

      <input type="button" value="Calculate" onclick="calculate()"><br>

      <h2 id="total-profit"></h2>
      <table>
        <thead>
          <tr>
            <th>Day</th>
            <th>Starting Amount</th>
            <th>Interest Earned</th>
            <th>Ending Amount</th>
          </tr>
        </thead>
        <tbody id="results">
        </tbody>
      </table>
    </form>

    <script>
      function calculate() {
        const initialAmount = parseFloat(document.getElementById("initial-amount").value);
        const dailyInterestRate = 0.8 / 100;
        const numDays = parseInt(document.getElementById("num-days").value);

        let currentAmount = initialAmount;
        let totalInterest = 0;
        let tableRows = "";

        for (let i = 1; i <= numDays; i++) {
          const dailyInterest = currentAmount * dailyInterestRate;
          const endingAmount = currentAmount + dailyInterest;
          totalInterest += dailyInterest;
          tableRows += "<tr><td>" + i + "</td><td>" + currentAmount.toFixed(2) + "</td><td>" + dailyInterest.toFixed(2) + "</td><td>" + endingAmount.toFixed(2) + "</td></tr>";
          currentAmount = endingAmount;
        }

        const totalProfit = totalInterest.toFixed(2);
        document.getElementById("total-profit").innerHTML = "Total Profit: ₹" + totalProfit;

        document.getElementById("results").innerHTML = tableRows;
      }
    </script>
  </body>
</html>

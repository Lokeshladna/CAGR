<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>CAGR Calculator</title>
  <script type="text/javascript" src="https://cdn.jsdelivr.net/npm/brython@3.9.5/brython.min.js"></script>
  <style>
    body { font-family: Arial; max-width: 400px; margin: 40px auto; padding: 20px; }
    input, button { width: 100%; padding: 10px; margin-top: 10px; }
    h2 { text-align: center; }
  </style>
</head>
<body onload="brython()">

  <h2>CAGR Calculator</h2>
  
  <label>Initial Value:</label>
  <input type="number" id="initial" placeholder="e.g. 10000">

  <label>Final Value:</label>
  <input type="number" id="final" placeholder="e.g. 20000">

  <label>Years:</label>
  <input type="number" id="years" placeholder="e.g. 5">

  <button onclick="calculate_cagr()">Calculate CAGR</button>

  <p id="result"></p>

  <script type="text/python">
    from browser import document

    def calculate_cagr(event=None):
        try:
            initial = float(document["initial"].value)
            final = float(document["final"].value)
            years = float(document["years"].value)

            if initial <= 0 or final <= 0 or years <= 0:
                raise ValueError("Inputs must be greater than 0")

            cagr = (final / initial) ** (1 / years) - 1
            percent = round(cagr * 100, 2)
            document["result"].text = f"CAGR: {percent}% per year"
        except Exception as e:
            document["result"].text = f"Error: {e}"

    document["result"].text = ""
  </script>

</body>
</html>

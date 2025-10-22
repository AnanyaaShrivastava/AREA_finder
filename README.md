
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Area Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f3f4f6;
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-top: 50px;
    }
    .container {
      background: white;
      padding: 25px;
      border-radius: 15px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      width: 300px;
      text-align: center;
    }
    input, select, button {
      margin: 10px 0;
      padding: 8px;
      width: 90%;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
      background-color: #2563eb;
      color: white;
      cursor: pointer;
      border: none;
    }
    button:hover {
      background-color: #1d4ed8;
    }
    #result {
      margin-top: 15px;
      font-weight: bold;
      color: #2563eb;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Area Calculator</h2>
    
    <label for="shape">Select Shape:</label>
    <select id="shape" onchange="toggleInputs()">
      <option value="square">Square</option>
      <option value="rectangle">Rectangle</option>
    </select>

    <div id="squareInputs">
      <input type="number" id="side" placeholder="Enter side length">
    </div>

    <div id="rectangleInputs" style="display:none;">
      <input type="number" id="length" placeholder="Enter length">
      <input type="number" id="breadth" placeholder="Enter breadth">
    </div>

    <button onclick="calculateArea()">Find Area</button>

    <div id="result"></div>
  </div>

  <script>
    function toggleInputs() {
      const shape = document.getElementById('shape').value;
      document.getElementById('squareInputs').style.display = shape === 'square' ? 'block' : 'none';
      document.getElementById('rectangleInputs').style.display = shape === 'rectangle' ? 'block' : 'none';
      document.getElementById('result').innerHTML = '';
    }

    function calculateArea() {
      const shape = document.getElementById('shape').value;
      let area;

      if (shape === 'square') {
        const side = parseFloat(document.getElementById('side').value);
        if (isNaN(side) || side <= 0) {
          document.getElementById('result').innerHTML = "Please enter a valid side length.";
          return;
        }
        area = side * side;
      } else {
        const length = parseFloat(document.getElementById('length').value);
        const breadth = parseFloat(document.getElementById('breadth').value);
        if (isNaN(length) || isNaN(breadth) || length <= 0 || breadth <= 0) {
          document.getElementById('result').innerHTML = "Please enter valid dimensions.";
          return;
        }
        area = length * breadth;
      }

      document.getElementById('result').innerHTML = `Area of the ${shape} is <strong>${area}</strong> square units.`;
    }
  </script>
</body>
</html>

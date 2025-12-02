# Ex06 BMI Calculator 

## AIM
To develop a responsive and interactive Body Mass Index (BMI) Calculator using React that allows users to input their height and weight, and calculates their BMI to categorize their health status (e.g., Underweight, Normal, Overweight, Obese).

## DESIGN STEPS

### STEP 1: Initialize React Project

<li>Create a new React app using create-react-app.</li>
<li>Install React Router using:</li>
npm install react-router-dom

### STEP 2: Set Up Routing

Create routing structure with react-router-dom:

<li>Home route (/) – Intro or Navigation</li>

<li>BMI Calculator route (/bmi)</li>

<li>Result route (/result)</li>

### STEP 3: Design the BMI Form Page

<li>Create a form to accept Height (in cm or m) and Weight (in kg).</li>

<li>On form submit, navigate to the result page with entered values via URL query params or context/state.</li>

## STEP 4: Handle Input Validation

<li>Check if height and weight are valid numbers.</li>

<li>Optionally, show error messages for invalid inputs.</li>

### STEP 5: Perform BMI Calculation

<li>In the result component:

<li>Extract height and weight from the route (URL or passed state).</li>

<li>Apply the BMI formula:</li>

![image](https://github.com/user-attachments/assets/ec785506-c96b-489e-8783-fb1a5d36101a)
​
 
<li>Convert height from cm to m if needed.</li></li>

### STEP 6: Display Result

<li>Show calculated BMI.</li>

<li>Show category based on BMI range:

<li>Underweight, Normal, Overweight, Obese, etc.</li></li>

### STEP 7: Navigation Options

<li>Provide a button to go back to the BMI form to calculate again.</li>

### STEP 8: Enhancements

<li>Add styling using CSS or Tailwind.</li>

## PROGRAM

## APP.JSX
```
import React, { useState } from "react";
import "./App.css";

function App() {
  const [height, setHeight] = useState("");
  const [weight, setWeight] = useState("");
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState("");

  const calculateBMI = (e) => {
    e.preventDefault();
    if (height > 0 && weight > 0) {
      const heightInMeters = height / 100;
      const result = (weight / (heightInMeters * heightInMeters)).toFixed(2);
      setBmi(result);

      if (result < 18.5) setCategory("Underweight");
      else if (result < 24.9) setCategory("Normal weight");
      else if (result < 29.9) setCategory("Overweight");
      else setCategory("Obese");
    } else {
      alert("Please enter valid numbers!");
    }
  };

  return (
    <div className="container">
      <div className="bmi-card">
        <h1>BMI Calculator</h1>
        <form onSubmit={calculateBMI}>
          <input
            type="number"
            placeholder="Height (cm)"
            value={height}
            onChange={(e) => setHeight(e.target.value)}
          />
          <input
            type="number"
            placeholder="Weight (kg)"
            value={weight}
            onChange={(e) => setWeight(e.target.value)}
          />
          <button type="submit">Calculate</button>
        </form>

        {bmi && (
          <div className="result">
            <h2>Your BMI: {bmi}</h2>
            <p>Category: {category}</p>
          </div>
        )}
      </div>
    </div>
  );
}

export default App;
```

## APP.CSS
```
body {
  margin: 0;
  font-family: "Poppins", sans-serif;
  background: linear-gradient(to right, #dbeafe, #f0fdf4);
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.bmi-card {
  background-color: white;
  padding: 40px;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  text-align: center;
  width: 350px;
}

h1 {
  color: #1e3a8a;
  margin-bottom: 20px;
}

input {
  width: 90%;
  padding: 10px;
  margin: 10px 0;
  border: 1px solid #ccc;
  border-radius: 6px;
  outline: none;
  font-size: 16px;
}

button {
  background-color: #2563eb;
  color: white;
  border: none;
  padding: 10px 25px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 16px;
}

button:hover {
  background-color: #1d4ed8;
}

.result {
  margin-top: 20px;
}

.result h2 {
  color: #2563eb;
}
```


## OUTPUT

<img width="1917" height="1198" alt="image" src="https://github.com/user-attachments/assets/9f7bd2bd-6eb4-43a8-8d1f-d55b4f0985bf" />
<img width="1900" height="1275" alt="image" src="https://github.com/user-attachments/assets/211515c9-bb2e-4fab-ae5d-d656d1719626" />
<img width="1897" height="1197" alt="image" src="https://github.com/user-attachments/assets/a59406e8-4db3-43c0-abad-42ebb5b2b7c7" />




## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.

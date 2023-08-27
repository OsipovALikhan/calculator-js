# simple calculator app that runs through node js terminal
const readline = require('readline');



const rl = readline.createInterface({

  input: process.stdin,

  output: process.stdout

});



let num1, operator, num2; // Declare variables to store user inputs



rl.question('Please type first number: ', (inputNum1) => {

  num1 = parseFloat(inputNum1);

  console.log('First number:', num1); // Display the entered first number



  rl.question('Please type operator (+, -, *, /): ', (inputOperator) => {

    operator = inputOperator;

    console.log('Operator:', operator); // Display the entered operator



    rl.question('Please type second number: ', (inputNum2) => {

      num2 = parseFloat(inputNum2);

      console.log('Second number:', num2); // Display the entered second number



      try {

        const result = calculate(num1, operator, num2);

        console.log('Result is:', result);

      } catch (error) {

        console.log('Error:', error.message);

      }



      rl.close();

    });

  });

});



function calculate(num1, operator, num2) {

  switch (operator) {

    case '+':

      return num1 + num2;

    case '-':

      return num1 - num2;

    case '*':

      return num1 * num2;

    case '/':

      if (num2 === 0) {

        throw new Error("Division by zero is not allowed");

      }

      return num1 / num2;

    default:

      throw new Error("Invalid operator");

  }

}

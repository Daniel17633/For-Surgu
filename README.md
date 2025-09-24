<!DOCTYPE html> 
<html lang="ru"> 
<head>
  <meta charset="UTF-8">
  <title>+++ Calculator</title> 
  <link href="style.css" rel="stylesheet"> 
</head>

<body> 

  <h1>Калькулятор Сложения</h1> 
  <h3>Введите два числа и нажмите сложить!</h3>

  <div class="calculator"> 

    <input type="number" class="n1" id="num1" placeholder="Введите 1-ое число">

    <br>

    <input type="number" class="n2" id="num2" placeholder="Введите 2-ое число">

    <br> 

    <button class="b-1" onClick="sumInputs()">Вычислить</button>
  
    <div>Ваш ответ</div>
    <div id="out-1"></div>

  </div> 

</body>
</html>
___________________________________________________________________________________
body {
    font-family: Arial, Helvetica, sans-serif;
    text-align: center;
    }

.calculator {
    background-color: Silver;
    padding: 40px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    display: inline-block;
    }

label, input, button {
    display: table-cell;
    margin: 10px 0;
    }

button {
    background-color: white;
    color: black;
    border: none;
    padding: 10px 20px;
    border-radius: 5px;
    cursor: pointer;
    }
    
    button:hover {
    background-color: black;
    color:white;
    }
________________________________________
function sumInputs() {

   let num1 = Number( document.getElementById("num1").value );
   let num2 = Number( document.getElementById("num2").value );
   
   document.getElementById("out-1").innerHTML = num1 + num2;
   
}










function sumInputs() {
    let input1 = document.getElementById("num1").value.trim();
    let input2 = document.getElementById("num2").value.trim();
    
    let errorMsg = "";
    
    // Проверяем первое поле
    if (input1 === "" || isNaN(Number(input1))) {
        errorMsg += "Ошибка в первом поле: введены буквы (или ничего) вместо цифр. ";
    }
    
    // Проверяем второе поле
    if (input2 === "" || isNaN(Number(input2))) {
        errorMsg += "Ошибка во втором поле: введены буквы (или ничего) вместо цифр. ";
    }
    
    // Если есть ошибки, выводим сообщение
    if (errorMsg !== "") {
        document.getElementById("out-1").innerHTML = errorMsg;
        document.getElementById("out-1").style.color = "red"; // Дополнительно: красный цвет для ошибки
        return;
    }
    
    // Если всё OK, вычисляем сумму
    let num1 = Number(input1);
    let num2 = Number(input2);
    let result = num1 + num2;
    
    document.getElementById("out-1").innerHTML = result;
    document.getElementById("out-1").style.color = "black"; // Сброс цвета для результата
}

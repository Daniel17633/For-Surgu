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
   let value1 = document.getElementById("num1").value.trim();
   let value2 = document.getElementById("num2").value.trim();
   
   let hasLetters1 = /[a-zA-Zа-яА-Я]/.test(value1);
   let hasLetters2 = /[a-zA-Zа-яА-Я]/.test(value2);
   
   if (hasLetters1 && hasLetters2) {
       document.getElementById("out-1").innerHTML = 'ошибка в обоих строках';
   } else if (hasLetters1) {
       document.getElementById("out-1").innerHTML = 'ошибка в 1 строке';
   } else if (hasLetters2) {
       document.getElementById("out-1").innerHTML = 'ошибка в 2 строке';
   } else {
       let num1 = Number(value1);
       let num2 = Number(value2);
       if (isNaN(num1) || isNaN(num2)) {
           document.getElementById("out-1").innerHTML = 'ошибка ввода'; // Дополнительная проверка на нечисловые значения без букв
       } else {
           document.getElementById("out-1").innerHTML = num1 + num2;


       }
   }
}
_____________________________________________________________________________________________________
#include <iostream>
#include <cmath>
using namespace std;

float add(float a, float b) {
    if (a == 0) {
        cout << "Деление на ноль!" << endl;
        return 0;
    }
    return -b / a;
}

int main()
{   
    int k, l, m;
    float result;
    
    cout << "Введите число k: ";
    cin >> k;
    
    cout << "Введите число l: ";
    cin >> l;
    
    cout << "Введите число m: ";
    cin >> m;
    
    int promegutok1 = max(pow(k, 2), l);
    int promegutok2 = max(pow(3, m), pow(l, 3));
    
    float x = add(max(promegutok1, pow(m, 0.5)), max(promegutok2, k + l));
    
    cout << "Результат: " << x << endl;
    return 0;
}            

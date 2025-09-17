<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <link rel="stylesheet" href="cssforsite.css">
  <title>Document</title>
</head>
<body>
  <div class="outer-block">
    <div class="left-block">
      <h1>Мои заметки</h1>
      <button class="newmark"><b>Новая заметка</button>
        <div class="tegs">Теги</div>
        <ul class="tags-list">
  <li>Все</li>
  <li>Идеи</li>
  <li>Личное</li>
  <li>Работа</li>
  <li>Список покупок</li>
</ul>
        </div>
        
    <input type="text" name="text" class="search" placeholder="Поиск">
<button type="button" class="buttonsearch">  
</button> 
      <button type="button">Сдать отчёт</button>
</body>
</html>

___________________________________________

body, html {
      height: 100%;
      margin: 0;
      padding: 0;
    }
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: #eaeaea;
      height: 100vh; /* чтобы flex работал корректно */
    }
    .outer-block {
      width: 1000px;
      height: 90vh;
      background-color: #ffffff;
      box-sizing: border-box;
      border-radius: 10px;
      display: flex; /* добавлено для горизонтального расположения внутренних блоков */
      overflow: hidden; /* чтобы скругления работали корректно */
    }
    .left-block {
      text-align:center;
      width: 370px; /* 33% от 1000px */
      height: 90vh;
      background-color: #F0F0F0;
      border-top-left-radius: 10px;
      border-bottom-left-radius: 10px;
      padding-top: 16px;
      padding-left: 8px;/* для отступов внутри */
      box-sizing: border-box;
      overflow-y: auto; /* если текста много, появится скролл */
      font-size:18px;
      position: relative;
    }

.newmark{
  background-color:#4499FF;
  color:#ffffff;
  border-radius:5px;
  padding: 16px 72px 16px 72px;
  border: none;
  outline: none;
  font-size:18px;
  font-weight: 500;
}

.tegs{
  font-size:24px;
  color:#74777B;
  position:absolute;  
  padding-left:30px;
  padding-top:50px;
}

.tags-list {
  padding-left:50px;
  margin-top: 100px;
  color: black;
  font-size: 21px;
  list-style: none;
  text-align:left;
}

li{
  padding:15px;
}

.tags-list li:hover {
  background-color: #f4f4f4;
  cursor: pointer;
  border-radius:15px;
  width:250px;
}

.search{
  width:500px;
  height:40px;
  color:#FCFCFC;
  padding-left:10px;
  border-radius:10px;
  background-color:#F4F4F4;
  border:none;
  margin:36px 0px 0px 36px;
  border-color:red;
}

input::placeholder{color: #74777B;}

input, select, textarea{
    color: black;
}

textarea:focus, input:focus {
    color: black;
}

.buttonsearch{
  color:blue;
  height:40px;
  width:40px;
  margin-top:20px;
  border:none;
  border-radius:10px;
  background-color:#4499FF;
  position:absolute;
  margin:36px 0px 0px 12px;
  background-image: url(https://img.icons8.com/?size=100&id=7695&format=png&color=FFFFFF);
  background-size:25px;
  background-repeat: no-repeat;
  background-position: center;
}


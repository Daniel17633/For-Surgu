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
        
    <div class="search-block">
  <input type="text" name="text" class="search" placeholder="Поиск" />
  <button type="button" class="buttonsearch"></button>
</div>
      <div class="notes-list">
  <div class="note">
    <div class="note-title">Идеи для проекта</div>
    <div class="note-date">2024-06-01</div>
    <div class="note-section">Идеи</div>
  </div>
  <div class="note">
    <div class="note-title">Личные планы</div>
    <div class="note-date">2024-05-28</div>
    <div class="note-section">Личное</div>
  </div>
  <div class="note">
    <div class="note-title">Список покупок</div>
    <div class="note-date">2024-06-02</div>
    <div class="note-section">Список покупок</div>
  </div>
</div>
</body>
</html>






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
  cursor: pointer; 
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
  border:none;
  border-radius:10px;
  background-color:#4499FF;
  background-image: url(https://img.icons8.com/?size=100&id=7695&format=png&color=FFFFFF);
  background-size:25px;
  background-repeat: no-repeat;
  background-position: center;
  margin-left: 12px;
}

.buttonsearch:hover{
  cursor:pointer;
}

.search-block {
  display: flex;
  align-items: center;
  margin: 36px 0 0 36px; 
}
.search {
  margin: 0; /* убираем margin сверху */
  width: 500px;
  height: 40px;
  color: #FCFCFC;
  padding-left: 10px;
  border-radius: 10px;
  background-color: #F4F4F4;
  border: none;
}

.notes-list {
  width: 565px; /* ширина чуть больше поля поиска */
  margin: 56px 0 0 36px; /* отступ сверху и слева, чтобы совпадало с поиском */
  background-color: #ffffff;
  border-radius: 10px;
  box-shadow: 0 0 8px rgba(0,0,0,0.1);
  padding: 14px;
  box-sizing: border-box;
}
.note {
  padding:24px 16px;
  border-bottom: 1px solid #ddd;
}
.note:last-child {
  border-bottom: none;
}
.note-title {
  font-weight: 600;
  font-size: 24px;
  color: #333;
}
.note-date, .note-section {
  font-size: 18px;
  color: #666;
  margin-top: 8px;
}

.note {
  background-color: #f9f9f9; /* светлый фон для заметки */
  border: 1px solid #ddd; /* рамка вокруг заметки */
  border-radius: 8px; /* скругление углов */
  padding: 20px 16px;
  margin-bottom: 16px; /* отступ между заметками */
  box-shadow: 0 2px 5px rgba(0,0,0,0.05); /* лёгкая тень для объёма */
}
.note:last-child {
  margin-bottom: 0; /* у последней заметки отступ снизу не нужен */
}

.note:hover{
  background-color:#4499FF;
   cursor: pointer; 
}

.note:hover .note-title {
  color: #FFFFFF; /* белый цвет заголовка */
}

.note:hover .note-date{
  color: #E0E0E0; /* светло-серый цвет для даты и раздела */
}
.note:hover .note-section {
  color:black;
  background-color:white;
}

.note {
  position: relative; /* добавлено для позиционирования .note-section */
  background-color: #f9f9f9;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 20px 16px;
  margin-bottom: 16px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.05);
}
.note-section {
  position: absolute;
  top: 16px; /* отступ от верхнего края заметки */
  right: 16px; /* отступ от правого края заметки */
  background-color: #F0F0F0; /* цвет фона прямоугольника */
  color: black;
  padding: 4px 12px;
  border-radius: 12px;
  font-size: 15px;
  font-weight: 600;
  white-space: nowrap; /* чтобы текст не переносился */
}


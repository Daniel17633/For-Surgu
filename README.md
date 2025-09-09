<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Document</title>
  <style>
    * {
      margin: 0;
      padding: 0;
    }

    .h1 {
      font-size: 24px;
    }

    .h2 {
      font-size: 24px;
    }

    .wrapper {
      max-width: 800px;
      margin: 0 auto;
    }

    .header {
      display: flex;
      gap: 30px;
      padding: 30px 0;
    }

    .header__info {
      flex-grow: 1;
      display: flex;
      flex-direction: column;
      justify-content: center;
      gap: 5px;
    }

    .header__contacts {
      display: flex;
      gap: 5px;
      flex-direction: column;
      justify-content: center;
      align-items: flex-end;
    }

    .about {
      margin-top: 20px;
    }

    .table {
      margin-top: 40px;
      display: grid;
      grid-template-columns: 1fr 1fr;
    }

    .table__hobbies {
      border: 1px solid #008000;
      border-radius: 10px 0 0 10px;
    }

    .table__hobbies-title,
    .table__social-title {
      border-bottom: 1px solid green;
      text-align: center;
      color: green;
      padding: 5px 0;
      font-weight: bold;
    }

    .table__social {
      border: 1px solid #008000;
      border-radius: 0 10px 10px 0;
    }

    .table__list {
      width: fit-content;
      margin: 0 auto;
    }

    .table__content {
      display: flex;
      align-items: center;
      justify-content: center;
      flex-grow: 1;
    }

    .table__list-items {
      padding-top: 17px;
    }

    .table__list-itemp {
      padding-bottom: 17px;
    }

    .table__list-item:hover {
      cursor: pointer;
      color: green;
    }

    .table__list-itemvk {
      padding-top: 26px;
    }

    .table__list-itemvk:hover {
      cursor: pointer;
      color: green;
    }

    .table__list-itemp:hover {
      cursor: pointer;
      color: green;
    }

    .table__list-items:hover {
      cursor: pointer;
      color: green;
    }

    .table__list-item>a {
      text-decoration: none;
      color: black;
    }

    .title {
      background: green;
      border-radius: 10px;
      text-align: center;
      color: white;
      font-weight: bold;
      padding: 5px 0;
      margin-top: 60px;
    }

    .technologies {
      display: flex;
      justify-content: space-between;
      margin-top: 20px;
    }

    .technologies__item {
      display: flex;
      flex-direction: column;
      gap: 10px;
      align-items: center;
      padding: 20px;
      border-radius: 10px;
      transition: all 0.5s ease-in-out;
    }

    .technologies__item>img {
      border-radius: 50%;
    }

    .technologies__item:hover {
      box-shadow: 0 4px 20px 0 #5a9645;
      cursor: pointer;
      background: green;
    }

    .feedback__title {
      max-width: 800px;
      background: green;
      text-align: center;
      color: white;
      font-weight: bold;
      padding: 5px 0;
      margin: 60px auto 0 auto;
      font-size: 16px;
      border-radius: 7px;
    }

    .feedback__form {
      max-width: 800px;
      margin: 0 auto;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
    }

    .feedback__input1,
    .feedback__input2 {
      width: 100%;
      box-sizing: border-box;
      border: 1.5px solid #ccc;
      border-radius: 7px;
      padding: 10px 12px;
      font-size: 14px;
      margin-top: 15px;
    }

    .feedback__textarea {
      grid-column: 1 / -1;
      width: 100%;
      box-sizing: border-box;
      border: 1.5px solid #ccc;
      border-radius: 7px;
      padding: 10px 12px;
      font-size: 14px;
      resize: vertical;
    }

    .feedback__button {
      background-color: green;
      color: white;
      border: none;
      border-radius: 7px;
      padding: 10px 30px;
      font-size: 16px;
      cursor: pointer;
      margin-top: 15px;
      transition: background-color 0.3s ease;
      width: fit-content;
      grid-column: 1 / -1;
      justify-self: center;
    }

    .feedback__button:hover {
      background-color: #447a34;
    }
  </style>
</head>

<body>
  <div class="wrapper">
    <header class="header">
      <img class="header__img" src="./images/avatar.jpg" alt="Аватар пользователя" />
      <div class="header__info">
        <h1 class="h1">Иван Петров</h1>
        <p>Frontend developer</p>
      </div>
      <div class="header__contacts">
        <h2 class="h2">Контакты</h2>
        <span>+79224122272</span>
        <span>email@mail.com</span>
      </div>
    </header>
    <hr />
    <p class="about">
      <b>Немного обо мне:</b> это текст-"рыба", часто используемый в печати и вэб-дизайне. Lorem Ipsum является
      стандартной
      "рыбой" для текстов на латинице с начала XVI века. В то время некий безымянный печатник создал большую коллекцию
      размеров и форм шрифтов, используя Lorem Ipsum для распечатки образцов. Lorem Ipsum не только успешно пережил без
      заметных изменений пять веков...
    </p>
    <div class="table">
      <div class="table__hobbies">
        <div class="table__hobbies-title">Хобби</div>
        <div class="table__content">
          <ul class="table__list">
            <li class="table__list-items">Чтение</li>
            <li class="table__list-item">Путешествия</li>
            <li class="table__list-item">Настольные игры</li>
            <li class="table__list-itemp">Плавание</li>
          </ul>
        </div>
      </div>
      <div class="table__social">
        <div class="table__social-title">Соц сети</div>
        <div class="table__content">
          <ol class="table__list">
            <li class="table__list-itemvk">VK</li>
            <li class="table__list-item">Inst</li>
            <li class="table__list-itemp">TG</li>
          </ol>
        </div>
      </div>
    </div>
    <div class="title">Интересующие технологии</div>
    <div class="technologies">
      <div class="technologies__item">
        <img src="./images/js.jpg" alt="JavaScript" />
        <span>JavaScript</span>
      </div>
      <div class="technologies__item">
        <img src="./images/js.jpg" alt="JavaScript" />
        <span>JavaScript</span>
      </div>
      <div class="technologies__item">
        <img src="./images/js.jpg" alt="JavaScript" />
        <span>JavaScript</span>
      </div>
      <div class="technologies__item">
        <img src="./images/js.jpg" alt="JavaScript" />
        <span>JavaScript</span>
      </div>
    </div>
  </div>
  <div class="feedback">
    <h2 class="feedback__title">Форма обратной связи</h2>
    <form class="feedback__form" action="#" method="post">
      <input type="text" name="name" class="feedback__input1" placeholder="Ваше имя" required />
      <input type="tel" name="phone" class="feedback__input2" placeholder="Телефон" required />
      <textarea name="question" class="feedback__textarea" placeholder="Ваш вопрос" required></textarea>
      <button type="submit" class="feedback__button">Отправить</button>
    </form>
  </div>
</body>

</html>

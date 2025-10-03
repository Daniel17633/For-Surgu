<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <link rel="stylesheet" href="projectcss.css" />
  <title>Document</title>
  <style>
    /* Дополнительные стили для исправления правой части */
    .right-block {
      flex: 1;
      box-sizing: border-box;
      position: relative;
      height: 100%;
    }
    .note-detail {
      display: none;
      width: 100%;
      height: 100%;
      padding: 36px;
      background-color: #f9f9f9;
      overflow-y: auto;
      box-sizing: border-box;
      position: absolute;
      top: 0;
      left: 0;
      z-index: 10;
    }
    .note-detail > div {
      width: 100%;
    }
    .detail-title {
      margin: 0;
      flex: 1;
      font-size: 24px;
      color: #333;
      font-weight: 600;
    }
    .detail-date, .detail-section {
      width: 100%;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      box-sizing: border-box;
      margin-bottom: 10px;
      font-size: 16px;
    }
    .detail-section {
      background-color: #F0F0F0;
      color: black;
    }
    .detail-content {
      width: 100%;
      min-height: 300px;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      box-sizing: border-box;
      font-family: inherit;
      resize: vertical;
      font-size: 14px;
      line-height: 1.5;
    }
    .detail-buttons {
      text-align: right;
      margin-top: 20px;
      width: 100%;
    }
    .detail-buttons button {
      padding: 10px 20px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-size: 16px;
      margin-left: 10px;
    }
    .back-btn, .cancel-detail-btn {
      background-color: #ccc;
      color: #333;
    }
    .save-detail-btn {
      background-color: #4499FF;
      color: #fff;
    }
    .search-block, .notes-list {
      position: relative;
      z-index: 1;
    }
  </style>
</head>
<body>
  <div class="outer-block">
    <div class="left-block">
      <h1>Мои заметки</h1>
      <button class="newmark"><b>Новая заметка</b></button>
      <div class="tegs">Теги</div>
      <ul class="tags-list">
        <li>Все</li>
        <li>Идеи</li>
        <li>Личное</li>
        <li>Работа</li>
        <li>Список покупок</li>
      </ul>
    </div>

    <div class="right-block">
      <div class="search-block">
        <input type="text" name="text" class="search" placeholder="Поиск" />
        <button type="button" class="buttonsearch"></button>
      </div>
      <div class="notes-list">
        <div class="note">
          <div class="note-title">Идеи для проекта</div>
          <div class="note-date">2024-06-01</div>
          <div class="note-section">Идеи</div>
          <div class="note-content" style="display: none;"></div>
        </div>
        <div class="note">
          <div class="note-title">Личные планы</div>
          <div class="note-date">2024-05-28</div>
          <div class="note-section">Личное</div>
          <div class="note-content" style="display: none;"></div>
        </div>
        <div class="note">
          <div class="note-title">Список покупок</div>
          <div class="note-date">2024-06-02</div>
          <div class="note-section">Список покупок</div>
          <div class="note-content" style="display: none;"></div>
        </div>
      </div>
      <!-- Блок для детального просмотра/редактирования заметки -->
      <div class="note-detail">
        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px;">
          <h2 class="detail-title"></h2>
          <button class="back-btn">Назад</button>
        </div>
        <div>
          <label style="display: block; margin-bottom: 5px; font-weight: bold;">Дата: </label>
          <input type="date" class="detail-date">
        </div>
        <div>
          <label style="display: block; margin-bottom: 5px; font-weight: bold;">Тег: </label>
          <input type="text" class="detail-section" readonly>
        </div>
        <div>
          <label style="display: block; margin-bottom: 5px; font-weight: bold;">Содержимое:</label>
          <textarea class="detail-content"></textarea>
        </div>
        <div class="detail-buttons">
          <button class="save-detail-btn">Сохранить</button>
          <button class="cancel-detail-btn">Отмена</button>
        </div>
      </div>
    </div>
  </div>

  <script>
    // Получаем элементы
    const searchInput = document.querySelector('.search');
    const searchBlock = document.querySelector('.search-block');
    const notesList = document.querySelector('.notes-list');
    const noteDetail = document.querySelector('.note-detail');
    const newMarkBtn = document.querySelector('.newmark');
    const tagsList = document.querySelectorAll('.tags-list li');

    // Функция фильтрации заметок по заголовку (работает только в списке)
    function filterNotes() {
      const query = searchInput.value.toLowerCase();
      const notes = notesList.querySelectorAll('.note');

      notes.forEach(note => {
        const title = note.querySelector('.note-title').textContent.toLowerCase();
        if (title.includes(query)) {
          note.style.display = '';
        } else {
          note.style.display = 'none';
        }
      });
    }

    // Обработчик поиска по вводу
    searchInput.addEventListener('input', filterNotes);

    // Функция показа списка заметок
    function showNotesList() {
      notesList.style.display = 'block';
      searchBlock.style.display = 'flex';
      noteDetail.style.display = 'none';
      filterNotes(); // Применяем текущий фильтр
    }

    // Функция показа детального просмотра/редактирования заметки
    function showNoteDetail(noteElement) {
      const title = noteElement.querySelector('.note-title').textContent;
      const date = noteElement.querySelector('.note-date').textContent;
      const section = noteElement.querySelector('.note-section').textContent;
      const content = noteElement.querySelector('.note-content').textContent || ''; // Если нет содержимого, пустая строка

      // Заполняем детальный вид
      noteDetail.querySelector('.detail-title').textContent = title;
      noteDetail.querySelector('.detail-date').value = date;
      noteDetail.querySelector('.detail-section').value = section;
      noteDetail.querySelector('.detail-content').value = content;

      // Скрываем список и поиск, показываем детальный вид
      searchBlock.style.display = 'none';
      notesList.style.display = 'none';
      noteDetail.style.display = 'block';

      // Обработчики кнопок в детальном виде
      const backBtn = noteDetail.querySelector('.back-btn');
      const saveBtn = noteDetail.querySelector('.save-detail-btn');
      const cancelBtn = noteDetail.querySelector('.cancel-detail-btn');

      // Функция возврата назад
      const goBack = () => {
        showNotesList();
      };

      backBtn.onclick = goBack;
      cancelBtn.onclick = goBack;

      // Сохранение изменений
      saveBtn.onclick = () => {
        const newTitle = noteDetail.querySelector('.detail-title').textContent;
        const newDate = noteDetail.querySelector('.detail-date').value;
        const newSection = noteDetail.querySelector('.detail-section').value;
        const newContent = noteDetail.querySelector('.detail-content').value;

        if (newDate) {
          // Обновляем оригинальную заметку
          noteElement.querySelector('.note-title').textContent = newTitle;
          noteElement.querySelector('.note-date').textContent = newDate;
          noteElement.querySelector('.note-section').textContent = newSection;
          noteElement.querySelector('.note-content').textContent = newContent;

          goBack(); // Возвращаемся к списку
        } else {
          alert('Дата обязательна!');
        }
      };
    }

    // Функция создания новой заметки
    function createNote(title, date, section, content = '') {
      const note = document.createElement('div');
      note.classList.add('note');

      const noteTitle = document.createElement('div');
      noteTitle.classList.add('note-title');
      noteTitle.textContent = title;

      const noteDate = document.createElement('div');
      noteDate.classList.add('note-date');
      noteDate.textContent = date;

      const noteSection = document.createElement('div');
      noteSection.classList.add('note-section');
      noteSection.textContent = section;

      const noteContent = document.createElement('div');
      noteContent.classList.add('note-content');
      noteContent.style.display = 'none';
      noteContent.textContent = content;

      note.appendChild(noteTitle);
      note.appendChild(noteDate);
      note.appendChild(noteSection);
      note.appendChild(noteContent);

      notesList.prepend(note); // Добавляем в начало списка

      // Добавляем обработчик клика для открытия детального вида
      note.addEventListener('click', () => showNoteDetail(note));
    }

    // Добавляем обработчики клика для существующих заметок
    document.addEventListener('DOMContentLoaded', () => {
      const existingNotes = notesList.querySelectorAll('.note');
      existingNotes.forEach(note => {
        // Добавляем note-content если его нет
        if (!note.querySelector('.note-content')) {
          const noteContent = document.createElement('div');
          noteContent.classList.add('note-content');
          noteContent.style.display = 'none';
          noteContent.textContent = '';
          note.appendChild(noteContent);
        }
        note.addEventListener('click', () => showNoteDetail(note));
      });
    });

    // Обработчик кнопки "Новая заметка"
    newMarkBtn.addEventListener('click', () => {
      // Создаем форму для ввода новой заметки
      const formOverlay = document.createElement('div');
      formOverlay.style.position = 'fixed';
      formOverlay.style.top = 0;
      formOverlay.style.left = 0;
      formOverlay.style.width = '100vw';
      formOverlay.style.height = '100vh';
      formOverlay.style.backgroundColor = 'rgba(0,0,0,0.5)';
      formOverlay.style.display = 'flex';
      formOverlay.style.justifyContent = 'center';
      formOverlay.style.alignItems = 'center';
      formOverlay.style.zIndex = 1000;

      const form = document.createElement('form');
      form.style.backgroundColor = '#fff';
      form.style.padding = '20px';
      form.style.borderRadius = '10px';
      form.style.width = '500px'; // Увеличили ширину для textarea
      form.style.maxHeight = '80vh';
      form.style.overflowY = 'auto';
      form.style.boxSizing = 'border-box';
      form.style.display = 'flex';
      form.style.flexDirection = 'column';
      form.style.gap = '12px';

      // Заголовок
      const titleLabel = document.createElement('label');
      titleLabel.textContent = 'Заголовок:';
      const titleInput = document.createElement('input');
      titleInput.type = 'text';
      titleInput.required = true;

      // Дата
      const dateLabel = document.createElement('label');
      dateLabel.textContent = 'Дата:';
      const dateInput = document.createElement('input');
      dateInput.type = 'date';
      dateInput.required = true;
      // По умолчанию сегодняшняя дата
      const today = new Date().toISOString().split('T')[0];
      dateInput.value = today;

      // Тег (раздел)
      const sectionLabel = document.createElement('label');
      sectionLabel.textContent = 'Тег:';
      const sectionSelect = document.createElement('select');
      sectionSelect.required = true;

      // Добавляем опции из списка тегов (кроме "Все")
      tagsList.forEach(li => {
        if (li.textContent !== 'Все') {
          const option = document.createElement('option');
          option.value = li.textContent;
          option.textContent = li.textContent;
          sectionSelect.appendChild(option);
        }
      });

      // Содержимое
      const contentLabel = document.createElement('label');
      contentLabel.textContent = 'Содержимое:';
      const contentTextarea = document.createElement('textarea');
      contentTextarea.rows = 10;
      contentTextarea.style.width = '100%';
      contentTextarea.style.padding = '8px';
      contentTextarea.style.border = '1px solid #ccc';
      contentTextarea.style.borderRadius = '5px';
      contentTextarea.style.boxSizing = 'border-box';
      contentTextarea.required = false;

      // Кнопки
      const buttonsDiv = document.createElement('div');
      buttonsDiv.style.display = 'flex';
      buttonsDiv.style.justifyContent = 'space-between';

      const submitBtn = document.createElement('button');
      submitBtn.type = 'submit';
      submitBtn.textContent = 'Добавить';
      submitBtn.style.backgroundColor = '#4499FF';
      submitBtn.style.color = '#fff';
      submitBtn.style.border = 'none';
      submitBtn.style.padding = '8px 16px';
      submitBtn.style.borderRadius = '5px';
      submitBtn.style.cursor = 'pointer';

      const cancelBtn = document.createElement('button');
      cancelBtn.type = 'button';
      cancelBtn.textContent = 'Отмена';
      cancelBtn.style.backgroundColor = '#ccc';
      cancelBtn.style.border = 'none';
      cancelBtn.style.padding = '8px 16px';
      cancelBtn.style.borderRadius = '5px';
      cancelBtn.style.cursor = 'pointer';

      buttonsDiv.appendChild(submitBtn);
      buttonsDiv.appendChild(cancelBtn);

      // Добавляем элементы в форму
      form.appendChild(titleLabel);
      form.appendChild(titleInput);
      form.appendChild(dateLabel);
      form.appendChild(dateInput);
      form.appendChild(sectionLabel);
      form.appendChild(sectionSelect);
      form.appendChild(contentLabel);
      form.appendChild(contentTextarea);
      form.appendChild(buttonsDiv);

      formOverlay.appendChild(form);
      document.body.appendChild(formOverlay);

      // Обработчик отмены
      cancelBtn.addEventListener('click', () => {
        document.body.removeChild(formOverlay);
      });

      // Обработчик отправки формы
      form.addEventListener('submit', (e) => {
        e.preventDefault();
        const title = titleInput.value.trim();
        const date = dateInput.value;
        const section = sectionSelect.value;
        const content = contentTextarea.value;

        if (title && date && section) {
          createNote(title, date, section, content);
          document.body.removeChild(formOverlay);
          searchInput.value = ''; // очищаем поиск
          filterNotes(); // обновляем фильтр
        }
      });
    });
  </script>
</body>
</html>

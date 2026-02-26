# Пошаговое обучение: Создание интерактивных HTML-документов для контент-проектов

## Введение

Это руководство научит вас создавать красивые, интерактивные HTML-документы. Вы научитесь работать с **HTML**, **CSS** и **JavaScript** для визуализации контента.

---

## Уровень 1: Фундамент (HTML)

### 1.1 Базовая структура HTML-документа

```html
<!DOCTYPE html>
<html>
<head>
    <title>Заголовок страницы</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
    <!-- Содержимое страницы -->
</body>
</html>
```

**Объяснение:**
- `<!DOCTYPE html>` — сообщает браузеру, что это HTML5
- `<head>` — служебная информация (заголовок, стили, мета-теги)
- `<body>` — всё, что видит пользователь

### 1.2 Основные теги для контента

| Тег | Назначение | Пример |
|-----|------------|--------|
| `<h1>`-`<h6>` | Заголовки | `<h1>Главный заголовок</h1>` |
| `<p>` | Абзац | `<p>Текст параграфа</p>` |
| `<div>` | Контейнер-блок | `<div class="box">...</div>` |
| `<span>` | Строчный контейнер | `<span class="highlight">текст</span>` |
| `<table>` | Таблица | Сложная структура (см. ниже) |
| `<img>` | Изображение | `<img src="icon.png" alt="описание">` |

### 1.3 Структура таблицы

```html
<table>
    <thead>
        <tr>
            <th>Заголовок 1</th>
            <th>Заголовок 2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Данные 1</td>
            <td>Данные 2</td>
        </tr>
    </tbody>
</table>
```

### 1.4 Атрибуты: классы и ID

```html
<div class="container" id="main-block">
    <!-- Класс используется для группы элементов -->
    <!-- ID уникальный для одного элемента -->
</div>
```

---

## Уровень 2: Стилизация (CSS)

### 2.1 Подключение CSS

**Способ 1: Внутренний стиль (в `<head>`)**
```html
<head>
    <style>
        body {
            background-color: white;
            color: black;
        }
    </style>
</head>
```

**Способ 2: Внешний файл**
```html
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```

### 2.2 Селекторы CSS

```css
/* По тегу */
body { font-family: Arial; }

/* По классу (самый частый способ) */
.container { width: 100%; }
.info-box { background: #f0f0f0; }

/* По ID */
#main-title { font-size: 24px; }

/* Вложенные селекторы */
.container p { color: blue; } /* Все p внутри .container */
```

### 2.3 CSS-переменные (кастомизация)

```css
:root {
    --main-color: #3498db;
    --text-color: #333;
    --bg-color: white;
}

body {
    background-color: var(--bg-color);
    color: var(--text-color);
}

.button {
    background: var(--main-color);
}
```

### 2.4 Flexbox для верстки

```css
.container {
    display: flex;
    justify-content: center; /* по горизонтали */
    align-items: center; /* по вертикали */
    gap: 20px; /* расстояние между элементами */
}
```

### 2.5 Медиа-запросы (адаптация под мобильные)

```css
/* Для экранов меньше 768px */
@media screen and (max-width: 768px) {
    body {
        font-size: 14px;
    }
    
    .container {
        flex-direction: column; /* вертикально на мобилках */
    }
}
```

---

## Уровень 3: Интерактивность (JavaScript)

### 3.1 Подключение JS

```html
<body>
    <!-- контент -->
    
    <script>
        // JS код прямо здесь
    </script>
    
    <!-- или подключить файл -->
    <script src="script.js"></script>
</body>
```

### 3.2 Переключение тем (как в нашем примере)

```javascript
function toggleTheme() {
    const body = document.body;
    const button = document.querySelector('.theme-toggle');
    
    if (body.classList.contains('dark-theme')) {
        body.classList.remove('dark-theme');
        button.textContent = '🌙 Тёмная тема';
        localStorage.setItem('theme', 'light');
    } else {
        body.classList.add('dark-theme');
        button.textContent = '☀️ Светлая тема';
        localStorage.setItem('theme', 'dark');
    }
}
```

### 3.3 Сохранение темы в localStorage

```javascript
document.addEventListener('DOMContentLoaded', function() {
    const savedTheme = localStorage.getItem('theme');
    
    if (savedTheme === 'dark') {
        document.body.classList.add('dark-theme');
    }
});
```

### 3.4 Работа с DOM (динамическое изменение страницы)

```javascript
// Найти элемент
const table = document.querySelector('table');
const headers = document.querySelectorAll('thead th');

// Добавить атрибут всем ячейкам
const cells = document.querySelectorAll('tbody td');
cells.forEach(cell => {
    cell.setAttribute('data-label', 'значение');
});
```

---

## Уровень 4: Структура проекта

### 4.1 Организация файлов

```
project/
│
├── index.html          # главная страница
├── styles.css          # все стили
├── script.js           # все скрипты
│
├── images/             # папка с картинками
│   ├── icon1.png
│   └── icon2.png
│
└── README.md           # документация
```

### 4.2 Комментарии в коде

```html
<!-- Это комментарий HTML - он не виден на странице -->
<div>Видимый контент</div>
```

```css
/* Это комментарий CSS */
.header {
    background: black; /* темный фон для шапки */
}
```

```javascript
// Это комментарий JavaScript (однострочный)

/*
Многострочный
комментарий
*/
```

---

## Уровень 5: Создание таблицы для shorts (наш случай)

### 5.1 Структура таблицы в HTML

```html
<div class="table-wrapper"> <!-- для скролла на мобилках -->
    <table>
        <thead>
            <tr>
                <th>#</th>
                <th>Название</th>
                <th>Описание</th>
                <th>Иконки</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td><strong>Входящие: Баламут</strong></td>
                <td>Описание short</td>
                <td>
                    <span class="icon-tag">envelope</span>
                    <span class="icon-tag">alert</span>
                </td>
            </tr>
        </tbody>
    </table>
</div>
```

### 5.2 Стили для таблицы

```css
table {
    border-collapse: collapse;
    width: 100%;
    border: 1px solid #ddd;
}

th {
    background: #f5f5f5;
    position: sticky;
    top: 0;
}

td {
    padding: 10px;
    border: 1px solid #ddd;
}

/* Специальные блоки */
.scripture-block {
    background: #ebf8ff;
    border-left: 4px solid #4299e1;
    padding: 8px;
}
```

### 5.3 Адаптация для мобильных

```css
@media screen and (max-width: 768px) {
    /* Превращаем таблицу в карточки */
    table, thead, tbody, tr, td {
        display: block;
    }
    
    thead {
        display: none; /* скрываем заголовки */
    }
    
    tr {
        margin-bottom: 20px;
        border: 1px solid #ddd;
    }
    
    td {
        display: flex;
        flex-direction: column;
    }
    
    td:before {
        content: attr(data-label); /* показываем название колонки */
        font-weight: bold;
        margin-bottom: 5px;
    }
}
```

---

## Уровень 6: Работа с данными

### 6.1 Создание массива данных (для динамической генерации)

```javascript
const shortsData = [
    {
        id: 1,
        title: "Входящие: Баламут — Гнусику",
        description: "Скрин письма...",
        icons: ["envelope", "alert"],
        scripture: "Пс. 5:3"
    },
    // ... еще 39 записей
];
```

### 6.2 Динамическое создание таблицы из данных

```javascript
function generateTable(data) {
    let html = '';
    
    data.forEach(item => {
        html += `
            <tr>
                <td>${item.id}</td>
                <td><strong>${item.title}</strong></td>
                <td>${item.description}</td>
                <td>${item.icons.map(icon => 
                    `<span class="icon-tag">${icon}</span>`
                ).join(' ')}</td>
            </tr>
        `;
    });
    
    document.querySelector('tbody').innerHTML = html;
}
```

### 6.3 Фильтрация и поиск

```javascript
function filterShorts(searchText) {
    return shortsData.filter(item => 
        item.title.toLowerCase().includes(searchText.toLowerCase())
    );
}

// Использование
const searchInput = document.querySelector('#search');
searchInput.addEventListener('input', (e) => {
    const filtered = filterShorts(e.target.value);
    generateTable(filtered);
});
```

---

## Уровень 7: Продвинутые техники

### 7.1 CSS Grid для сложных макетов

```css
.dashboard {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
}

@media (max-width: 768px) {
    .dashboard {
        grid-template-columns: 1fr; /* один столбец на мобилках */
    }
}
```

### 7.2 Анимации и переходы

```css
.button {
    transition: all 0.3s ease;
}

.button:hover {
    transform: scale(1.05);
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
}

@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

.element {
    animation: fadeIn 1s ease;
}
```

### 7.3 Работа с LocalStorage

```javascript
// Сохранить данные
localStorage.setItem('key', 'value');

// Получить данные
const data = localStorage.getItem('key');

// Удалить
localStorage.removeItem('key');

// Очистить всё
localStorage.clear();
```

---

## Чек-лист создания документа

### Этап 1: Планирование
- [ ] Определить структуру контента
- [ ] Продумать адаптацию под мобильные
- [ ] Выбрать цветовую схему

### Этап 2: HTML
- [ ] Создать базовую структуру
- [ ] Добавить мета-теги
- [ ] Разметить контент (таблицы, заголовки)
- [ ] Добавить классы для стилизации

### Этап 3: CSS
- [ ] Определить CSS-переменные
- [ ] Стилизовать таблицы
- [ ] Сделать адаптивную верстку
- [ ] Добавить микро-интерактивность (hover)

### Этап 4: JavaScript
- [ ] Переключение тем
- [ ] Сохранение темы в localStorage
- [ ] Адаптация таблицы под мобильные (data-label)
- [ ] Динамическая генерация контента (если нужно)

### Этап 5: Тестирование
- [ ] Проверить на десктопе (Chrome, Firefox)
- [ ] Проверить на мобильных (iPhone, Android)
- [ ] Проверить переключение темы
- [ ] Убедиться, что данные сохраняются

---

## Полезные ресурсы

1. **Документация:**
   - [MDN Web Docs](https://developer.mozilla.org/ru/) — лучшая документация
   - [CSS Tricks](https://css-tricks.com/) — советы по CSS

2. **Иконки:**
   - [Flaticon](https://www.flaticon.com/) — тысячи бесплатных иконок
   - [Font Awesome](https://fontawesome.com/) — иконочный шрифт

3. **Цвета:**
   - [Coolors](https://coolors.co/) — генератор цветовых схем
   - [Color Hunt](https://colorhunt.co/) — готовые палитры

4. **Шрифты:**
   - [Google Fonts](https://fonts.google.com/) — бесплатные шрифты

5. **Валидация:**
   - [W3C Validator](https://validator.w3.org/) — проверка HTML
   - [CSS Validator](https://jigsaw.w3.org/css-validator/) — проверка CSS

---

## Заключение

Ключевые моменты:

1. **HTML** — структура и контент
2. **CSS** — внешний вид и адаптация
3. **JavaScript** — интерактивность и логика
4. **LocalStorage** — сохранение настроек
5. **Медиа-запросы** — работа на всех устройствах

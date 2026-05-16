## Как всё устроено


Любой мини-проект состоит из трёх файлов в одной папке:
- `index.html` – структура страницы
- `style.css` – внешний вид
- `script.js` – интерактивность

В `index.html` мы подключаем CSS в `<head>` и JavaScript перед закрывающим тегом `</body>` (или с атрибутом `defer`). Так браузер сначала построит страницу, а потом запустит программу.

---





```markdown
---

## 📦 HTML — строительные блоки

Тег пишется в угловых скобках и обычно бывает парным: открывающий `<tag>` и закрывающий `</tag>`. Всё, что между ними — содержимое тега.

### Самые нужные теги

**Заголовки** — от самого большого к самому маленькому:

```html
<h1>Самый главный заголовок</h1>
<h2>Заголовок поменьше</h2>
<h3>Ещё меньше</h3>
```

*Обычно на странице только один `<h1>`, а остальных сколько угодно.*

**Абзацы и просто текст:**

```html
<p>Это абзац. Браузер сам сделает отступы сверху и снизу.</p>
<span>А это строчный элемент — он не переносится на новую строку.</span>
```

**Кнопки — их можно сделать двумя способами:**

```html
<!-- Способ 1: тег button (чаще всего используем его) -->
<button>Просто кнопка</button>

<!-- Способ 2: тег input с типом button (старый вариант) -->
<input type="button" value="Тоже кнопка">
```

*Разница: внутрь `<button>` можно положить что угодно (текст, картинку), а `<input>` — только надпись из атрибута `value`.*

**Поля ввода — тег `<input>` с разными типами:**

```html
<input type="text" placeholder="Обычный текст">       <!-- просто текст -->
<input type="number" placeholder="Только числа">       <!-- только цифры -->
<input type="password" placeholder="Пароль">           <!-- звёздочки вместо букв -->
<input type="email" placeholder="Твой email">          <!-- проверяет, есть ли @ -->
<input type="color">                                   <!-- выбор цвета -->
<input type="range" min="0" max="100">                 <!-- ползунок -->
<input type="checkbox">                                <!-- галочка -->
<input type="radio" name="group1">                     <!-- переключатель (один из группы) -->
```

*Всегда давай полям `placeholder` — это подсказка, которая видна, пока поле пустое.*

**Многострочный текст:**

```html
<textarea rows="4" cols="30" placeholder="Напиши что-нибудь длинное..."></textarea>
```

**Выпадающий список:**

```html
<select>
  <option>Красный</option>
  <option>Зелёный</option>
  <option>Синий</option>
</select>
```

**Картинка:**

```html
<img src="путь/к/картинке.png" alt="Описание картинки">
```

*Атрибут `alt` важен: если картинка не загрузится, покажется этот текст. И скринридеры для незрячих людей его читают.*

**Ссылка:**

```html
<a href="https://example.com">Нажми сюда</a>
<a href="https://example.com" target="_blank">Откроется в новой вкладке</a>
```

**Списки:**

```html
<ul>                          <!-- неупорядоченный (маркированный) список -->
  <li>Первый пункт</li>
  <li>Второй пункт</li>
</ul>

<ol>                          <!-- упорядоченный (нумерованный) список -->
  <li>Первый</li>
  <li>Второй</li>
</ol>
```

**Контейнеры — `<div>` и `<span>`:**

```html
<div class="box">Я блочный контейнер — занимаю всю ширину</div>
<span class="highlight">Я строчный — только сколько нужно тексту</span>
```

*`<div>` — для крупных блоков (карточка, секция), `<span>` — для кусочка текста внутри абзаца.*

### Что такое id и class

У каждого тега могут быть атрибуты `id` и `class`. Это как имя и нашивка на форме.

```html
<button id="submitBtn">Отправить</button>   <!-- id — уникальное имя, только одно на всю страницу -->
<button class="red-btn">Кнопка 1</button>   <!-- class — метка, может быть у многих элементов -->
<button class="red-btn">Кнопка 2</button>   <!-- ещё одна с тем же классом -->
```

*Используй `id`, когда элемент один и ты будешь искать его из JavaScript. Используй `class`, когда нужно задать стиль нескольким элементам сразу.*

### Таблицы — когда нужно показать данные в строках и столбцах

```html
<table>
  <tr>                          <!-- строка таблицы (table row) -->
    <th>Имя</th>                <!-- заголовок столбца (жирный по центру) -->
    <th>Возраст</th>
  </tr>
  <tr>
    <td>Аня</td>                <!-- обычная ячейка -->
    <td>14</td>
  </tr>
  <tr>
    <td>Боря</td>
    <td>15</td>
  </tr>
</table>
```

### Форма — чтобы собрать несколько полей и отправить

```html
<form>
  <input type="text" placeholder="Имя">
  <input type="email" placeholder="Почта">
  <button type="submit">Отправить</button>   <!-- type="submit" отправляет форму -->
</form>
```

*Когда ты просто вешаешь `addEventListener` на кнопку в форме, ставь кнопке `type="button"`, иначе страница может перезагрузиться.*

---



## 🎨 CSS — одежда для страницы

CSS говорит браузеру, как именно выглядит каждый элемент: какого он цвета, какого размера, где стоит.

### Как подключить стили к элементу

**Способ 1 — через class (самый частый):**
```css
.my-button {
  background-color: blue;
  color: white;
}
```
```html
<button class="my-button">Синяя кнопка</button>
```

**Способ 2 — через id (для уникальных элементов):**
```css
#special-button {
  background-color: red;
}
```
```html
<button id="special-button">Красная кнопка</button>
```

*В CSS перед именем класса ставят точку `.`, перед id — решётку `#`.*

**Способ 3 — прямо по названию тега:**
```css
button {
  border-radius: 8px;    /* повлияет на ВСЕ кнопки на странице */
}
```

### Цвет текста, цвет фона и прозрачность

```css
.text-block {
  color: white;                       /* цвет текста */
  background-color: darkblue;         /* цвет фона */
}

.half-visible {
  opacity: 0.5;                       /* полупрозрачный (от 0 до 1) */
}
```

*Цвет можно задавать названием (`red`, `steelblue`), HEX-кодом (`#ff0000`), RGB (`rgb(255, 0, 0)`) или RGBA с прозрачностью (`rgba(255, 0, 0, 0.5)`).*

### Размеры — px, проценты, vw, vh, em

Единицы измерения говорят браузеру, в чём ты задаёшь размер.

```css
.box {
  width: 300px;            /* фиксированная ширина в пикселях */
  height: 200px;           /* фиксированная высота в пикселях */
}

.half-box {
  width: 50%;              /* половина ширины родителя (меняется с размером окна) */
}

.fullscreen {
  width: 100vw;            /* ровно ширина всего окна браузера */
  height: 100vh;           /* ровно высота всего окна браузера */
}
```

*Когда использовать:*
- `px` — когда нужен точный размер (иконка, аватарка, отступы);
- `%` — когда хочешь, чтобы блок подстраивался под родителя;
- `vw` / `vh` — для секций на весь экран.

### Отступы — margin и padding

Представь коробку с подарком:
- `padding` — поролон внутри коробки, от края коробки до самого подарка.
- `margin` — расстояние от этой коробки до других коробок на столе.

```css
.card {
  padding: 20px;           /* отступы внутри элемента, от рамки до содержимого */
  margin: 30px;            /* отступы снаружи, до соседних элементов */
}
```

*Можно задать отступы по каждой стороне отдельно:*
```css
.card {
  padding-top: 10px;
  padding-right: 20px;
  padding-bottom: 10px;
  padding-left: 20px;
  /* короткая запись того же самого: padding: 10px 20px; (верх-низ, право-лево) */
}
```

### Границы и закругления

```css
.box {
  border: 2px solid black;           /* толщина | стиль | цвет */
  border-radius: 15px;               /* скругление углов */
}

.circle {
  width: 100px;
  height: 100px;
  border-radius: 50%;                /* идеальный круг (50% от размера) */
}
```

### Тень

```css
.card {
  box-shadow: 4px 4px 10px rgba(0, 0, 0, 0.3);  /* сдвигX сдвигY размытие цвет */
}

.text-shadow {
  text-shadow: 2px 2px 4px gray;                 /* тень для текста */
}
```

### Выравнивание

**Горизонтальное выравнивание текста:**
```css
p {
  text-align: center;    /* left | center | right | justify */
}
```

**Центрирование блока по горизонтали:**
```css
.container {
  width: 600px;
  margin: 0 auto;        /* автоматические отступы слева и справа — блок по центру */
}
```

**Flexbox — мощный инструмент для раскладки (вместо таблиц и float):**
```css
.parent {
  display: flex;
  justify-content: center;   /* горизонтальное выравнивание детей */
  align-items: center;       /* вертикальное выравнивание детей */
  gap: 20px;                 /* расстояние между детьми */
}
```

*Варианты `justify-content`: `flex-start` (прижать к началу), `flex-end` (к концу), `center`, `space-between` (раскидать с пустотой между), `space-around` (пустота вокруг каждого).*

### Hover — стиль при наведении курсора

Псевдокласс `:hover` срабатывает, когда мышь оказывается над элементом.

```css
button {
  background-color: royalblue;
  color: white;
  transition: background-color 0.3s;   /* чтобы смена цвета была плавной */
}

button:hover {
  background-color: darkblue;          /* цвет меняется при наведении */
  cursor: pointer;                     /* курсор становится ладошкой */
}
```

### Transition — плавные переходы

`transition` делает изменение любого CSS-свойства плавным.

```css
.box {
  width: 100px;
  height: 100px;
  background-color: tomato;
  transition: all 0.5s ease;           /* все свойства меняются плавно за 0.5 секунды */
}

.box:hover {
  width: 200px;                        /* при наведении ширина плавно увеличится */
  background-color: gold;              /* и цвет плавно поменяется */
}
```

*Синтаксис: `transition: свойство длительность тип_анимации;`*
*Типы анимации: `ease` (плавно), `linear` (равномерно), `ease-in` (ускорение), `ease-out` (замедление).*

### Градиенты — плавный переход между цветами

Градиент задаётся как значение `background` или `background-image`.

```css
.header {
  background: linear-gradient(to right, red, orange, yellow);
  /*  направление (to right / to bottom / 45deg), потом список цветов */
}

.button {
  background: linear-gradient(180deg, #ffffff, #dddddd);
}
```

*Можно использовать угол в градусах (`45deg`) или ключевые слова (`to right`, `to bottom left`).*

### Шрифты

```css
body {
  font-family: 'Arial', sans-serif;    /* основной шрифт, если нет — запасной */
  font-size: 16px;                     /* размер шрифта */
  font-weight: bold;                   /* жирность (normal, bold, 400, 700) */
  line-height: 1.5;                    /* межстрочный интервал (1.5 = полтора) */
}
```

*Безопасные шрифты, которые есть везде: `Arial`, `Verdana`, `Georgia`, `Courier New`, `Times New Roman`.*

### Фон страницы — цвет или картинка

```css
body {
  background-color: #f0f0f0;                         /* просто цвет */
  background-image: url('фон.png');                  /* картинка */
  background-size: cover;                            /* картинка растягивается на весь экран */
  background-repeat: no-repeat;                      /* не повторяется */
  background-position: center;                       /* по центру */
}
```

### Псевдоэлементы ::before и ::after — декоративные штучки

Позволяют добавить украшение (иконку, линию) без лишнего HTML.

```css
.important::before {
  content: "⭐ ";                  /* этот текст появится перед содержимым элемента */
}
```

---



## 🧩 Как собрать всё вместе — типичная карточка

Вот готовый рецепт красивой карточки с использованием многих приёмов сразу.

**HTML:**
```html
<div class="card">
  <h2>Заголовок карточки</h2>
  <p>Описание товара или новости. Здесь может быть любой текст.</p>
  <button class="card-btn">Подробнее</button>
</div>
```

**CSS:**
```css
.card {
  width: 280px;
  padding: 20px;
  margin: 20px auto;
  background: linear-gradient(135deg, #ffffff, #e0e0ff);
  border-radius: 12px;
  box-shadow: 4px 4px 12px rgba(0, 0, 0, 0.2);
  text-align: center;
  font-family: Arial, sans-serif;
}

.card h2 {
  color: #333;
  margin-bottom: 10px;
}

.card p {
  color: #666;
  font-size: 14px;
  line-height: 1.4;
}

.card-btn {
  padding: 10px 24px;
  background-color: royalblue;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s ease;
}

.card-btn:hover {
  background-color: darkblue;
}
```

*Разбери этот пример по кусочкам — здесь собрано почти всё, что описано выше. Меняй цвета, размеры, тени и смотри, что получается!*

---



## 🔧 Важные мелочи, о которых часто забывают

- **Сбрасывай стандартные отступы**, если они мешают:
  ```css
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  ```
  *`box-sizing: border-box` делает так, чтобы `padding` и `border` не увеличивали размер блока сверх заданной ширины.*

- **Прячем элемент полностью:**
  ```css
  .hidden {
    display: none;               /* элемент исчезает и не занимает места */
  }
  .invisible {
    visibility: hidden;          /* элемент не видно, но место остаётся */
  }
  ```

- **Делаем элемент строчным или блочным:**
  ```css
  .inline-block {
    display: inline-block;       /* стоит в строке, но можно задать ширину и высоту */
  }
  .block {
    display: block;              /* занимает всю ширину */
  }
  ```

---



## ✨ Шпаргалка по горячим клавишам в редакторе (VS Code)

- `Ctrl + S` — сохранить файл (делай это часто!)
- `Ctrl + Z` — отменить последнее действие
- `Ctrl + /` — закомментировать строку
- `Alt + стрелка вверх/вниз` — передвинуть строку
- `Ctrl + D` — выделить следующее такое же слово
- Напиши `!` и нажми `Tab` — появится заготовка HTML-страницы
```
```

## 1. Самая первая заготовка
Эти три файла — твой чистый лист. С них можно начинать любой пример или свой проект.

**index.html**
```html
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Мой проект</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Привет, мир!</h1>
  <script src="script.js" defer></script>
</body>
</html>
```

**style.css**
```css
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
  text-align: center;
  padding-top: 50px;
}
```

**script.js**
```js
// Пока пусто, здесь будет магия
```

---

## 2. Приветственная кнопка (alert, события, функция)
Представь, что кнопка — это дверной звонок. Мы вешаем на него «слушатель», и когда нажимают, запускается функция, которая показывает всплывающее окошко `alert`.

**index.html** (внутри `<body>` вместо `<h1>`)
```html
<button id="helloBtn">Нажми меня</button>
```

**style.css** (добавь к тому, что уже есть)
```css
button {
  padding: 10px 20px;
  font-size: 18px;
  cursor: pointer;
}
```

**script.js**
```js
function sayHello() {
  alert('Привет, друг! Рад, что ты зашел.');
}

const button = document.getElementById('helloBtn');
button.addEventListener('click', sayHello);
```

**Что здесь происходит:**
- `function sayHello() { ... }` — мы создали собственную команду (функцию) с именем `sayHello`. Внутри неё — вызов `alert`.
- `document.getElementById('helloBtn')` — находим на странице элемент с атрибутом `id="helloBtn"`.
- `button.addEventListener('click', sayHello)` — говорим браузеру: «когда случится событие `click` (щелчок) на кнопке, выполни функцию `sayHello`». Обрати внимание: название функции передаётся без круглых скобок.

---

## 3. Угадай число (условный оператор if, поле ввода, DOM)
Научим страницу принимать решение. Если пользователь ввёл число больше 10 — говорим «Много!», иначе — «Нормально».

**index.html** (внутри `<body>`)
```html
<input type="number" id="numberInput" placeholder="Введи число">
<button id="checkBtn">Проверить</button>
<p id="message"></p>
```

**style.css** (добавь)
```css
input {
  padding: 8px;
  font-size: 16px;
  margin-right: 10px;
}
#message {
  font-weight: bold;
  margin-top: 20px;
}
```

**script.js**
```js
function checkNumber() {
  const input = document.getElementById('numberInput');
  const messageElement = document.getElementById('message');
  const value = parseInt(input.value, 10);

  if (value > 10) {
    messageElement.textContent = 'Ого, много!';
  } else {
    messageElement.textContent = 'В самый раз.';
  }
}

const checkBtn = document.getElementById('checkBtn');
checkBtn.addEventListener('click', checkNumber);
```

**Что здесь происходит:**
- Получаем значение из поля ввода: `input.value` всегда строка. `parseInt` превращает её в целое число.
- `if (условие) { ... } else { ... }` — условная конструкция. Если число больше 10, выполняется первый блок, иначе — второй.
- `messageElement.textContent = '...'` — меняет текст внутри тега `<p>`. Это самый безопасный способ вставить обычный текст в элемент.

---

## 4. Кричалка (работа со строками)
Мы берём текст, делаем его большими буквами, прибавляем восклицательные знаки и даже считаем его длину.

**index.html**
```html
<input type="text" id="textInput" placeholder="Введи что-нибудь">
<button id="shoutBtn">Закричать!</button>
<p id="shoutResult"></p>
<p id="lengthResult"></p>
```

**style.css** (по желанию, можно использовать тот же input и button)

**script.js**
```js
function shout() {
  const input = document.getElementById('textInput');
  const shoutElement = document.getElementById('shoutResult');
  const lengthElement = document.getElementById('lengthResult');

  const originalText = input.value;
  const shoutedText = originalText.toUpperCase() + '!!!';
  const textLength = originalText.length;

  shoutElement.textContent = shoutedText;
  lengthElement.textContent = 'В этом тексте ' + textLength + ' символов.';
}

const shoutBtn = document.getElementById('shoutBtn');
shoutBtn.addEventListener('click', shout);
```

**Что здесь происходит:**
- `originalText.toUpperCase()` — превращает все буквы строки в заглавные.
- `+ '!!!'` — склеивание (конкатенация) строк. Получаем кричащую версию.
- `originalText.length` — возвращает количество символов в строке (даже пробелы считает!).
- Результаты записываем в разные абзацы через `textContent`.

---

## 5. Цветной переключатель (изменение стилей через JS)
Меняем цвет фона всей страницы по нажатию на кнопку. Показываем, как JS управляет CSS-свойствами.

**index.html**
```html
<button id="colorBtn">Сменить фон</button>
```

**style.css**
```css
button {
  padding: 10px 20px;
  font-size: 18px;
  cursor: pointer;
}
```

**script.js**
```js
function changeBackground() {
  document.body.style.backgroundColor = 'lightcoral';
}

const colorBtn = document.getElementById('colorBtn');
colorBtn.addEventListener('click', changeBackground);
```

**Что здесь происходит:**
- `document.body` — доступ к тегу `<body>`.
- `.style.backgroundColor` — через точку мы обращаемся к CSS-свойству `background-color` (в JavaScript дефисы заменяются на верблюжью нотацию: `background-color` → `backgroundColor`).
- Каждый раз при клике цвет становится `lightcoral`. Если хочешь переключать туда-сюда, можно использовать условие (как в примере 3).

---

## 6. Волшебный квадрат (анимация через CSS transition + события мыши)
Сделаем красивый плавный переход цвета при наведении курсора. Вся анимация — это CSS, а JavaScript только говорит браузеру, какое событие слушать.

**index.html**
```html
<div id="magicBox"></div>
```

**style.css**
```css
#magicBox {
  width: 150px;
  height: 150px;
  background-color: steelblue;
  margin: 30px auto;
  transition: background-color 0.4s ease;
}
```

**script.js**
```js
const box = document.getElementById('magicBox');

box.addEventListener('mouseenter', function() {
  box.style.backgroundColor = 'tomato';
});

box.addEventListener('mouseleave', function() {
  box.style.backgroundColor = 'steelblue';
});
```

**Что здесь происходит:**
- В CSS задано свойство `transition: background-color 0.4s ease;` — оно делает любое изменение цвета фона плавным в течение 0.4 секунды.
- `mouseenter` — событие «курсор зашёл на элемент».
- `mouseleave` — событие «курсор покинул элемент».
- Внутри обработчиков мы меняем `style.backgroundColor`. Браузер сам плавно анимирует это изменение.

---

## 7. Исчезающий блок (классы и classList, событие click)
Тоже анимация, но теперь мы не трогаем стили напрямую, а добавляем или убираем готовый CSS-класс. Это удобно, когда нужно поменять не одно свойство, а целый набор.

**index.html**
```html
<button id="toggleBtn">Показать / Спрятать</button>
<div id="ghostBox" class="visible"></div>
```

**style.css**
```css
#ghostBox {
  width: 150px;
  height: 150px;
  background-color: mediumseagreen;
  margin: 20px auto;
  transition: opacity 0.5s ease;
}
.visible {
  opacity: 1;
}
.hidden {
  opacity: 0;
}
```

**script.js**
```js
function toggleVisibility() {
  const box = document.getElementById('ghostBox');
  box.classList.toggle('hidden');
}

const toggleBtn = document.getElementById('toggleBtn');
toggleBtn.addEventListener('click', toggleVisibility);
```

**Что здесь происходит:**
- У блока изначально есть класс `visible` (прозрачность 1). Класс `hidden` делает блок полностью прозрачным (`opacity: 0`).
- `box.classList.toggle('hidden')` — волшебный метод: если класса `hidden` нет, он добавляется; если есть — убирается.
- За счёт `transition: opacity 0.5s ease;` прозрачность меняется плавно. Получается эффект появления и исчезновения.

---

## 8. Супер-герой (ООП: классы и объекты)
Объектно-ориентированное программирование позволяет создавать шаблоны (классы), по которым потом штампуются персонажи, машины, да что угодно. У каждого персонажа есть свои свойства (имя, сила) и действия (методы).

**index.html**
```html
<button id="heroBtn">Создать героя</button>
<p id="heroInfo"></p>
```

**style.css** (используем готовые стили для button и p)

**script.js**
```js
class Hero {
  constructor(name, power) {
    this.name = name;
    this.power = power;
  }

  introduce() {
    return 'Я ' + this.name + ', моя суперсила – ' + this.power + '!';
  }
}

function createHero() {
  const hero1 = new Hero('Молния', 'скорость');
  const hero2 = new Hero('Ледяной', 'заморозка');
  const infoElement = document.getElementById('heroInfo');

  infoElement.textContent = hero1.introduce() + ' А также ' + hero2.introduce();
}

const heroBtn = document.getElementById('heroBtn');
heroBtn.addEventListener('click', createHero);
```

**Что здесь происходит:**
- `class Hero { ... }` — объявляем класс, как чертёж для героя.
- `constructor(name, power)` — специальный метод, который вызывается при создании нового объекта. Он записывает полученные параметры в свойства `this.name` и `this.power`.
- `introduce()` — обычный метод, который возвращает строку с представлением героя.
- `new Hero('Молния', 'скорость')` — создаёт конкретного героя по чертежу, подставляя свои имя и силу.
- Два объекта `hero1` и `hero2` существуют независимо, у каждого свои свойства. Вызываем их метод `introduce()` и выводим на страницу.

---

## А теперь собери свой проект!
Ты вспомнил все основные инструменты. Теперь ты можешь:
- взять заготовку из первого примера,
- добавить на страницу свои кнопки, поля ввода и блоки,
- скопировать нужные кусочки JavaScript и подправить их под свою идею.



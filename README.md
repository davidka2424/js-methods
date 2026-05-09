

## Как всё устроено
Любой мини-проект состоит из трёх файлов в одной папке:
- `index.html` – структура страницы
- `style.css` – внешний вид
- `script.js` – интерактивность

В `index.html` мы подключаем CSS в `<head>` и JavaScript перед закрывающим тегом `</body>` (или с атрибутом `defer`). Так браузер сначала построит страницу, а потом запустит программу.

---

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

Не бойся смешивать: например, поле ввода + условие + изменение стилей + анимация — и получится мини-игра. Самое главное — пробуй, ошибайся и исправляй. У тебя есть эта шпаргалка, а значит, всё получится!

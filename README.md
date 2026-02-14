
# Лабораторная работа №9  
## Адаптивная верстка: Медиа-запросы

---

## Цель работы  
Изучить принципы адаптивной верстки и медиа-запросов. В конце работы потребуется создать адаптивную страницу портфолио, которая корректно отображается на всех устройствах.

---

## Теоретические основы

- **Адаптивная верстка** — это подход, при котором дизайн и контент автоматически подстраиваются под размер экрана устройства (компьютер, планшет, смартфон).
- **Медиа-запросы (Media Queries)** — это техника CSS, позволяющая применять разные стили в зависимости от характеристик устройства (ширина экрана, ориентация, разрешение и т.д.).

---

## Синтаксис медиазапросов
```css
@media (условие) {
  /* стили для этого условия */
}
```

---

## Контрольные точки (breakpoints)

| Устройство                      | Ширина экрана             | Тип верстки               |
|---------------------------------|---------------------------|-------------------------|
| Мобильные устройства            | до 767px                  | Mobile First            |
| Планшеты                       | от 768px до 991px        | Mobile/Tablet First   |
| Десктопы                       | от 992px до 1199px      | Desktop First           |
| Большие дисплеи               | 1200px и более           | Large Desktop           |

> **Рекомендация:** используйте Mobile First — начинайте стили с маленьких экранов, а расширяйте для больших.

---

## Структура проекта

- **Создание рабочей директории**  
  Откройте Visual Studio Code и выполните команды:

  ```bash
  mkdir Lab9_Adaptive_FIO
  cd Lab9_Adaptive_FIO
  touch index.html styles.css README.md
  mkdir img
  ```

- **Подключение директории в VS Code**  
  Откройте папку через Explorer (Ctrl + B → Open Folder).

- **Инициализация Git**  
  ```bash
  git init -b main
  git add .
  git commit -m "Initial commit"
  ```

- **Подключение к GitHub (репозиторий создайте заранее)**  
  ```bash
  git remote add origin <URL_вашего_репозитория>
  git push -u origin main
  ```

---

## Создание адаптивной страницы

### Шаг 1. Создание HTML-файла (`responsive.html`)

Пример базовой структуры страницы:

```html
<!DOCTYPE html>
<html lang="ru-RU">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Адаптивный макет</title>
<link rel="stylesheet" href="responsive.css" />
</head>
<body>
<header class="header">
<div class="logo">Логотип</div>
<nav class="nav">
<a href="#">Главная</a>
<a href="#">Услуги</a>
<a href="#">Портфолио</a>
<a href="#">Контакты</a>
</nav>
</header>

<main class="main">
<section class="hero">
<h1>Добро пожаловать!</h1>
<p>Адаптивная верстка на Flexbox и Grid</p>
</section>

<section class="features">
<div class="feature">
<h3>Flexbox</h3>
<p>Одномерная раскладка для меню, карточек</p>
</div>
<div class="feature">
<h3>Grid</h3>
<p>Двумерная сетка для сложных макетов</p>
</div>
<div class="feature">
<h3>Media Queries</h3>
<p>Адаптация под любые устройства</p>
</div>
</section>

<section class="cards">
<article class="card">
<img src="https://via.placeholder.com/300x200" alt="Изображение 1" />
<h3>Карточка 1</h3>
<p>Описание первой карточки</p>
</article>
<article class="card">
<img src="https://via.placeholder.com/300x200" alt="Изображение 2" />
<h3>Карточка</h3>
<p>Описание второй карточки</p>
</article>
<article class="card">
<img src="https://via.placeholder.com/300x200" alt="Изображение 3" />
<h3>Карточка 3</h3>
<p>Описание третьей карточки</p>
</article>
</section>
</main>

<footer class="footer">
<p>&copy; 2026 Адаптивная верстка. Все права защищены.</p>
</footer>
</body>
</html>
```

### Шаг 2. Создание CSS-стилей (`responsive.css`)

Пример базовых стилей и медиа-запросов:

```css
/* Общие стили */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: Arial, sans-serif;
  line-height: 1.6;
}
/* Изображения */
img {
  max-width: 100%;
  height: auto;
  display: block;
}

/* Header - Мобильный дизайн (Mobile First) */
.header {
  background-color: #333;
  color: white;
  padding: 15px 20px;
  display: flex;
  flex-direction: column;
  gap: 15px;
}
.logo {
  font-size: 24px;
  font-weight: bold;
}
.nav {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.nav a {
  color: white;
  text-decoration: none;
  padding: 10px;
  background-color: #555;
  border-radius: 5px;
  text-align: center;
}
.nav a:hover {
  background-color: #777;
}

/* Hero */
.hero {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 60px 20px;
  text-align: center;
}
.hero h1 {
  font-size: 32px;
  margin-bottom: 15px;
}

/* Features */
.features {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 40px 20px;
  background-color: #f5f5f5;
}
.feature {
  background-color: white;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  text-align: center;
}
.feature h3 {
  margin-bottom: 10px;
  color: #333;
}

/* Карточки */
.cards {
  display: grid;
  grid-template-columns: 1fr;
  gap: 20px;
  padding: 40px 20px;
}
.card {
  background-color: white;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}
.card h3, .card p {
  padding: 15px;
}
.card h3 {
  color: #333;
}

/* Футер */
.footer {
  background-color: #333;
  color: white;
  text-align: center;
  padding: 20px;
}

/* Медиазапросы для адаптивности */

/* Планшеты и больше (от 768px) */
@media (min-width: 768px) {
  .header {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }
  .nav {
    flex-direction: row;
    gap: 15px;
  }
  .features {
    flex-direction: row;
  }
  .cards {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Десктопы (от 992px) */
@media (min-width: 992px) {
  .hero h1 {
    font-size: 48px;
  }
  .cards {
    grid-template-columns: repeat(3, 1fr);
  }
  .main {
    max-width: 1200px;
    margin: 0 auto;
  }
}

/* Большие дисплеи (от 1200px) */
@media (min-width: 1200px) {
  .header, .footer {
    padding-left: calc((100% - 1200px) / 2);
    padding-right: calc((100% - 1200px) / 2);
  }
}
```

---



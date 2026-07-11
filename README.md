# Yearle

Ежедневная игра-головоломка: угадай **год** исторического события по четырём независимым подсказкам. Аналог Wordle, но для дат.

Собрано на [Vite](https://vitejs.dev/) + [React](https://react.dev/). Единственные зависимости — `react` и `react-dom`; вся вёрстка на инлайн-стилях, без Tailwind и прочих библиотек.

## Локальный запуск

Нужен [Node.js](https://nodejs.org/) версии 18 или новее.

```bash
npm install     # установить зависимости
npm run dev     # запустить локальный сервер (http://localhost:5173)
```

Другие команды:

```bash
npm run build     # собрать продакшн-версию в папку dist/
npm run preview   # локально посмотреть собранную версию
```

## Как выложить на GitHub

1. Создай на GitHub новый пустой репозиторий (без README, .gitignore и лицензии).
2. В папке проекта выполни:

```bash
git init
git add .
git commit -m "Yearle: первая версия"
git branch -M main
git remote add origin https://github.com/ВАШ_ЛОГИН/ВАШ_РЕПОЗИТОРИЙ.git
git push -u origin main
```

Папка `node_modules` и сборка `dist` в репозиторий не попадут — они уже в `.gitignore`.

## Как задеплоить на Vercel

Vercel сам распознаёт проекты на Vite, никакой отдельной настройки не требуется.

1. Зайди на [vercel.com](https://vercel.com) и войди через свой аккаунт GitHub.
2. Нажми **Add New → Project** и выбери загруженный репозиторий.
3. Vercel сам определит:
   - **Framework Preset:** Vite
   - **Build Command:** `npm run build`
   - **Output Directory:** `dist`
4. Нажми **Deploy** — через минуту сайт будет доступен по адресу вида `ваш-проект.vercel.app`.

Каждый следующий `git push` в ветку `main` будет автоматически обновлять сайт.

## Структура проекта

```
.
├── index.html          # точка входа HTML
├── package.json        # зависимости и команды
├── vite.config.js      # конфигурация Vite
├── .gitignore
└── src/
    ├── main.jsx        # монтирование React-приложения
    ├── index.css       # минимальный сброс стилей
    └── Yearle.jsx      # сама игра (компонент и база событий)
```

## База событий

Вся база подсказок хранится прямо в `src/Yearle.jsx`:

- `ALL_DATA` — основная тема «Все темы»;
- `SCIENCE_DATA` — тема «🔬 Наука»;
- `THEMES` — сопоставление тем с их данными.

Каждая запись — это `{ year, facts: [...] }` с четырьмя независимыми фактами о событиях данного года.

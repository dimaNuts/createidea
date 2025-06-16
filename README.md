# createidea

# База

## Создание React приложения с помощью Vite

### Цели урока

- Использовать Vite для создания React приложения
- Запустить приложение в режиме разработки
- Посмотреть на приложение в браузере
- Поменять что-то в коде и посмотреть на результат
- Бегло осмотреть структуру созданного приложения

### Шаги

- `pnpm create vite webapp --template react-ts ` — создать Vite приложение с React
- `cd webapp` — перейти в папку с созданным приложением
- `pnpm i` - установка пакетов

### Выводы

- React — библиотека полезная для создания интерактивных пользовательских интерфейсов
- Альтернативы React: Vue, Angular, Svelte
- Vite нужен для того, чтобы удобно разрабатывать и собирать React приложения
- Альтернативы Vite: Create React App, Next.js, Webpack

## HTML теги

### Цели урока

- Познакомиться с основными HTML тегами
- Познакомиться с JSX

### Выводы

- HTML тег структурная единица веб-страницы
- HTML тег имеет название и может иметь атрибуты
- Самые популярные HTML теги: html, head, body, div, p, span, b, br, h1, h2, h3, h4, a, input, button
- JSX — это специальный JavaScript синтаксис для генерации HTML

## React и JavaScript

### Цели урока

- Выучить JavaScript
- Подружиться с React

### Шаги

- создать структуру данных `ideas`- массив объектов в `App.tsx`
- добавить ключ `key={idea.nick}` для массива в jsx структуре

### Вывод

- Выполняйте реальные задачи, создавайте реальные проекты. В процессе вы поймёте теорию. Не делайте наоборот. Выученное и неприменённое знание забудется. Знание, полученное во время решения реальных задач, закрепляется надёжно

### Полезные ссылки

https://learn.javascript.ru — бесплатный учебник по JavaScript

https://reactjs.org/docs/getting-started.html — официальная документация React

## Автоматическое форматирование кода через Prettier

### Шаги

- `pnpm i -D prettier` — установить Prettier в dev зависимости
- создать конфиг.файл `.prettierrc.yml`
- добавить в package.json скрипт ` "prettify": "prettier --log-level warn --cache --write src/**/*.{ts,tsx,js,json,yml,scss} !**/{node_modules,dist}/**/*"`
- `pnpm prettify` — отформатировать все файлы проекта

## Создание Node.js приложения на TypeScript

### Цели урока

- Сформировать конфиг тайпскипта
- Создать минимальное приложение на Node.js
- Зафиксировать версию Node.js
- Перезапускать приложение автоматически при изменении кода
- Сбилдить приложение
- Запустить сбилженное приложение

### Шаги

- `mkdir backend`— создать папку для бэкенда
- `cd backend` — перейти в папку с бэкендом
- создать package.json
- `pnpm i -D typescript ts-node` установить typescript, ts-node
- создать .\src\index.ts
- `pnpm exec tsc --init` создать файл backend/tsconfig.json
- `pnpm exec ts-node .\src\index.ts` - запуск index.ts
- `pnpm i -D ts-node-dev` - установить пакет для запуска сервера разработки, который автоматически транспилирует ваши файлы .ts в .js всякий раз, когда вы что-то редактируете.
- `pnpm i -D @types/node` - установить типы для node
- `pnpm i -D rimraf `- установить пакет, который при билде будет удалять папку dist
- `pnpm i -D prettier` — установить Prettier в dev зависимости
- вынести файл в общую папку `.prettierrc.yml`
- добавить в package.json скрипт ` "prettify": "prettier --log-level warn --cache --write src/**/*.{ts,tsx,js,json,yml,scss} !**/{node_modules,dist}/**/*"`
- `pnpm prettify` — отформатировать все файлы проекта

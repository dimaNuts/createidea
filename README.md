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

# Бэкенд-фронтенд

## Создание express приложения

### Цели урока

- Первратить бэкенд в процесс, обрабатывающий входящие запросы
- Создать проверочный эндпоинт с помощью express

### Шаги

- `pnpm i express` — установить express
- `pnpm i -D @types/express` — установить типы для express
- создать get-запрос на endpoint `/ping` с ответом `pong`

## Создание эндпоинта, возвращающего JSON

### Цель урока

- Создать эндпоинт, который будет возвращать список идей в формате JSON

### Шаги

- скопировать массив `ideas` webapp/src/App.tsx -> backend/index.ts
- добавить endpoint с адресом `/ideas`

### Выводы

- JSON — это формат данных, который используется для обмена данными между разными системами, очень похожий на обычный JavaScript объект
- Будучи TypeScript фулстек разработчиком удобнее всего использовать tRPC для общения между клиентом и сервером
- Используя tRPC вы будете быстрее разрабатывать, благодаря автодополнению кода и согласованности типов на фронте и бэке

## Добавление tRPC в бэкенд

### Цель урока

- Настроить серверную часть для работы с tRPC

### Шаги

- `pnpm i @trpc/server` - установить tRPC для сервера
- создать файл - `src/trpc.ts`
- создать функцию `getIdeas`, как объект `trpcRouter`, которую мы будем вызывать с фроненда на бэкенде
- перенести массив идей `src/index.ts` в файл - `src/trpc.ts`
- подключить `trpcRouter` к серверу `expressApp`
- экспортировать тип `trpcRouter`, для того, чтобы синхронизировать типы на фронтенде

### Выводы

- tRPC эндпоинты будут доступны по адресам вроде http://localhost:3000/trpc/getIdeas
- Однако, нам не надо думать об адресах эндпоинтов, мы должны относится к эндпоинтам, как к функциям, которые мы вызываем с фронтенда на бэкенде

### Полезная ссылка

https://trpc.io — официальный сайт tRPC

## Добавление tRPC во фронтенд

### Цели урока

- Добавить tRPC в webapp
- Запросить тайп-сейф данные с бэкенда
- Настроить монорепу с помощью pnpm

### Шаги

- `cd webapp && pnpm i @trpc/client @trpc/react-query @tanstack/react-query` — установить tRPC и его зависимости для клиента(трпс-клиент, адаптер для реакта, реакт-квери)
- создать webapp/src/lib/trpc.tsx (.tsx-файл будет содержать react-компонент)
- импортировать `createTRPCReact` и создать `trpc`, после чего на фронтенде будет доступно клиентское trpc, которое будет знать о всех типах с бэкенда, для этого, нужно ей о этих типах сообщить `<TrpcRouter>`
- Настроить монорепу с помощью pnpm, для этого, создать файл `pnpm-workspace.yaml`, описать в нём название пакетов(папок-backend/webapp). В
  `webapp/package.json` добавить в зависимости `"@ideanick/backend": "workspace:*"`. В
  `backend/package.json` переименовать `name` в `"@ideanick/backend"`. Создать `package.json` на верхнет уровне `createida/package.json`. Запустить `pnpm i`.
- создать два клиента `queryClient`- управляет логикой запросов(не типами) и `trpcClient`- должен знать где ендпоинт для всех trpc-роутеров
- создать компонент `TrpcProvider`, который будет сообщать о нашет приложении в react.
- `cd backend && pnpm i cors` — установить cors для бэкенда.
- `pnpm i -D @types/cors`- установить типы cors

### Выводы

- tRPC прекрасный инструмент для TypeScript фулстек разработки
- Многие вещи делаются только в начале проекта, и потом вы к ним не притрагиваетесь. Когда вы начинаете новый проект, вы просто копируете все эти сложные штуки и старого. Даже если вам сейчас не совсем понятно, как они работают, вы естественным образом с ними разберётесь, когда будете их использовать.

### Полезные ссылки

https://trpc.io — официальный сайт tRPC

# Качество кода

## Проверка типов

### Цель урока

- Создать скрипт для проверки типов, чтобы быть уверенным в том, что ваш код скорее всего работает

### Шаги

- Создать в `backend/package.json` поле `"types": "tsc --noEmit --project ./tsconfig.json"`
- Создать в `webapp/package.json` поле `"types": "tsc --noEmit --project ./tsconfig.app.json && tsc --noEmit --project ./tsconfig.node.json"`
- `pnpm types` — проверить типы

## Создание скриптов для монорепы

### Цели урока

- Вынести общие дев-зависимости в корневой package.json
- Завести общие скрипты для всех приложений монорепы, чтобы было удобнее работать

### Шаги

- `"scripts": {
  "b": "pnpm --filter @ideanick/backend",
  "w": "pnpm --filter @ideanick/webapp",
  "dev": "pnpm -r --parallel dev",
  "types": "concurrently \"pnpm b types\" \"pnpm w types\"",
  "prettify": "pnpm -r --parallel prettify"
}` - создать в корневом package.json

- `pnpm i -w -D concurrently` — установить concurrently для запуска нескольких скриптов одновременно

## Стандартизация стиля TypeScript кода с помощью ESLint

### Цель урока

- Стандартизировать стиль кода, чтобы снизить когнитивную нагрузку разработчика

### Шаги

- убрать поля `eslint` в webapp/package.json `"devDependencies": {
  "@types/react": "^19.1.2",
  "@types/react-dom": "^19.1.2",
  "@vitejs/plugin-react": "^4.4.1",
  "prettier": "^3.5.3",
  "vite": "^6.3.5"
}`
- `pnpm i -w -D eslint eslint-config-prettier eslint-plugin-import eslint-plugin-prettier eslint-plugin-react globals prettier-eslint typescript-eslint` -установить пакеты в корневой package.json

- создать `eslint.config.js`, `webapp/eslint.config.mjs`, `backend/eslint.config.mjs`
- редактируем backend/tsconfig.json
- добавить в корневой package.json `"type": "module"`
- создать папку .vscode
- добавить в backend/package.json
  `"lint": "eslint --cache --cache-location ./node_modules/.cache/.eslintcache --ext .ts ."`
- добавить в webapp/package.json
  `"lint": "eslint --cache --cache-location ./node_modules/.cache/.eslintcache --ext .ts,.tsx ."`
- добавить в package.json
  `"lint": "concurrently 'pnpm b lint' 'pnpm w lint'"`

### Вывод

- ESLint — это инструмент для статического анализа кода

## Автоматический вызов проверок и фиксов при коммите

### Цель урока

- Причёсывать и проверять код на стильность автоматчиески при коммите, чтобы гадкий код физически не мог попасть в репозиторий

### Шаги

- `pnpm i -w -D lint-staged`
- создать в корневой папке .git-hooks
- создать в папке .git-hooks файл pre-commit
- через wsl(у кого винда) выполнить chmod +x pre-commit
- `pnpm i`
- создать `.lintstagedrc.yml`, `webaap/.lintstagedrc.yml`,
  `backend/.lintstagedrc.yml`

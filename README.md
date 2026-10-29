# SkillSwap

Сервис для обмена навыками. Пользователь регистрируется в несколько шагов, указывает, чем готов поделиться, публикует навыки и находит людей для обмена. Пользователи могут искать навыки через фильтры, добавлять их в избранное, отправлять запросы на обмен и получать уведомления.

Учебный командный проект. Деплоя пока нет, данные берутся из моков в `public/db/`, серверной части нет.

## Стек

- React 19, TypeScript
- Vite 7, SCSS-модули
- Redux Toolkit и React Redux
- React Router 6
- React Hook Form и Yup для форм
- date-fns и react-day-picker для дат, react-dropzone для загрузки файлов, react-image-gallery для галереи
- Storybook 10, ESLint, Stylelint, Prettier

## Как поднять проект

### 1. Установка зависимостей

```bash
npm install
```

### 2. Запуск dev-сервера

```bash
npm run dev
```

### Другие команды

| Команда | Описание |
| --- | --- |
| `npm run build` | Проверка типов через `tsc` и сборка в `dist/` |
| `npm run preview` | Просмотр собранной версии |
| `npm run lint` | Проверка ESLint |
| `npm run lint:styles` | Проверка стилей Stylelint |
| `npm run format` | Форматирование Prettier |
| `npm run storybook` | Storybook на `http://localhost:6006` |

Тесты пока не написаны, `npm test` только выводит заглушку.

## Структура проекта

Проект построен по методологии Feature-Sliced Design:

```
src/
├── app/            # инициализация: App, роутер, store, защищенные маршруты
├── pages/          # страницы: главная, навык, профиль, авторизация, ошибки
├── widgets/        # крупные блоки интерфейса: шапка, футер, формы, модальные окна
├── features/       # пользовательские сценарии: auth, фильтры, избранное, уведомления, модальные окна
├── entities/       # бизнес-сущности: skill, user, request, exchange, notification, city, category
└── shared/         # переиспользуемое: UI-компоненты, хуки, стили, шрифты, иконки
public/
└── db/             # моки: users.json, skills.json, city.json, category.json, notifications.json
```

Алиасы импорта: `@app`, `@pages`, `@widgets`, `@features`, `@entities`, `@shared`.

## Моя зона ответственности

- **Переиспользуемые UI-компоненты** в `src/shared/ui`:
  - `SearchInput` (`shared/ui/search`)
  - `DropdownListUI` (`shared/ui/dropdown-list`) в трех режимах: обычный список, список с чекбоксами и список с поиском и фильтрацией.
- **Страница навыка** (`pages/skill`): перевел данные с моков на Redux store.
- **Завершающий шаг регистрации** (`pages/authorize`): модальное окно подтверждения, сохранение данных в store и переход на страницу созданного навыка.
- **Работа с Git в команде**: ветки под задачи, отслеживание задач, разрешение конфликтов слияния.

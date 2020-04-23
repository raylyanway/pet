
WIP
ДЛЯ РАЗРАБОТЧИКОВ ПРОСТЫХ ПРИЛОЖЕНИЙ

1.  [На чём мы пишем](#writing)
1.  [Чем мы собираем](#build)
1.  [Тестирование](#testing)
1.  [Линтинг кода и форматирование](#linting)
1.  [Библиотеки для конкретных задач](#common)
1.  [Какая структура должна быть в папке с компонентом, как называть файлы, типы, что экспортить?](#structure)
    1.  [Структура для папки с компонентами в простом проекте](#structure-simple)
1.  [Где мне взять переменные для цветов?](#color)
1.  [Где мне взять иконки?](#icon)
    1.  [Как подключить?](#icon-where)
1.  [Как мне называть классы для компонентов?](#class)
1.  [Как импортировать компоненты из модулей, которые экспортируют много React-компонентов?](#import)
1.  [Использование callback-функций в компонентах](#callback)
1.  [Поддерживаемые браузеры](#browser)
1.  [Что мы НЕ используем?](#unused)
1.  [Типизация](#typing)

# ✍️ На чем мы пишем<a name="writing"></a>

-   [Typescript](https://www.typescriptlang.org/)
-   [React](https://github.com/facebook/react)
-   [Redux](https://redux.js.org/)
-   [cssModules](https://github.com/css-modules/css-modules) + [postCSS](https://postcss.org/)

# 🏗️ Чем мы собираем<a name="build"></a>

-   [yarn](https://yarnpkg.com/) для установки зависимостей
-   [arui-scripts](https://github.com/alfa-laboratory/arui-scripts) для проектов
-   [library-utils](https://github.com/alfa-laboratory/library-utils) или [rollup]() (пока концепт) для библиотек

# 🧪 Тестирование<a name="testing"></a>

-   `data-test-id` мы называем так
-   [react-testing-library](https://github.com/testing-library/react-testing-library)
-   [jest](https://jestjs.io/)
-   [cypress](https://www.cypress.io/)

# 💾 Линтинг кода и форматирование<a name="linting"></a>

-   [eslint](https://eslint.org/)
-   [stylelint](https://github.com/stylelint/stylelint)
-   [commitlint](https://github.com/conventional-changelog/commitlint)
-   [prettier](https://prettier.io/)
-   [arui-presets-lint](https://github.com/alfa-laboratory/arui-presets-lint) Все настройки тут

# 🏦 Библиотеки для конкретных задач<a name="common"></a>

-   [date-fns](https://date-fns.org/) для работы с датами
-   [axios](https://github.com/axios/axios) для запросов на сервер. ВНИМАНИЕ!!! В приложении у вас должно быть минимум явного вызова axios. 99% случаев покроет [библиотекка шаремых сервисов](http://git.moscow.alfaintra.net/projects/RET/repos/retail-front-services/browse/src/api)
-   [lodash](https://lodash.com/) утилитарные функции общего назначения
-   [qrcode.react](https://github.com/zpao/qrcode.react) для генерации QR-кодов

# 🧬 Какая структура должна быть в папке с компонентом, как называть файлы, типы, что экспортить?<a name="structure"></a>

## Структура для папки с компонентами в простом проекте<a name="structure-simple"></a>

```
my-component/
  index.tsx
  index.module.css
  private-component/
    index.tsx
    index.module.css
```

# 🌈 Где мне взять переменные для цветов?<a name="color"></a>

В библиотеке [core-components](https://github.com/alfa-laboratory/core-components).

[Файл с цветами](https://github.com/alfa-laboratory/core-components/blob/master/packages/vars/colors.css)

# 🖼️ Где мне взять иконки?<a name="icon"></a>

-   [git](https://github.com/alfa-laboratory/icons)
-   [figma](https://www.figma.com/file/QoGuPDB1hAMoMMqsQQ4Mx7lB/Icons?node-id=3882%3A144)

## Как подключить?<a name="icon-where"></a>

```
yarn add @alfalab/icons
```

импорт через PascalCase: `Имя-из-figma`+`Icon`

# 📛 Как мне называть классы для компонентов?<a name="class"></a>

На текущий момент формируется это место [здесь](https://github.com/alfa-laboratory/tools)
Пока можно брать функции форматирования [отсюда](http://git.moscow.alfaintra.net/projects/EF/repos/arui-private/browse/src/lib/formatters.ts) (к примеру, `pluralize`)

# 🛎️ Как импортировать компоненты из модулей, которые экспортируют много React-компонентов?<a name="import"></a>

К компонентам стоит обращаться напрямую, используя запись через точку

```
// bad
import { Typography } from 'newclick-components';
import React from 'react';

const { Title } = Typography;

export const MyComponent = () => (
   <Title>Заголовок</Title>
);

// good
import { Typography } from 'newclick-components';
import React from 'react';

export const MyComponent = () => (
   <Typography.Title>Заголовок</Typography.Title>
);
```

# 📞 Использование callback-функций в компонентах<a name="callback"></a>

```
// bad
return <Button onClick={() => setShowActions(!showActions)} />;

// good
const toggleActions = () => setShowActions(!showActions);

return <Button onClick={toggleActions} />;
```

# 🖥 Поддерживаемые браузеры<a name="browser"></a>

| <img src="./images/edge.svg" alt="IE / Edge" width="24px" height="24px" /></br>IE / Edge | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/firefox/firefox_48x48.png" alt="Firefox" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)</br>Firefox | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png" alt="Chrome" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)</br>Chrome | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/safari/safari_48x48.png" alt="Safari" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)</br>Safari | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/opera/opera_48x48.png" alt="Opera" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)</br>Opera | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/yandex/yandex_48x48.png" alt="Yandex Browser" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)</br>Yandex Browser |
| ---------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p align="center">IE11, Edge</p>                                                         | <p align="center">последние 2 версии</p>                                                                                                                                                                          | <p align="center">последние 2 версии</p>                                                                                                                                                                      | <p align="center">последние 2 версии</p>                                                                                                                                                                      | <p align="center">последние 2 версии</p>                                                                                                                                                                  | <p align="center">последние 2 версии</p>                                                                                                                                                                                      |

# 📕 Что мы НЕ используем?<a name="unused"></a>

-   [CSS grid](https://developer.mozilla.org/ru/docs/Web/CSS/grid)

# 🆎 Типизация<a name="typing"></a>

-   пример именование типа пропсов в либе: `SelectProps`

# Что покрывать юнит тестами?

# Как писать документацию?

# Нужно оттопыривать data-test-id (как, мотивация)

# Где мы храним часто используемые функции?

# Как оттопырить data-test-id тестеровщику если очень надо?

# В моем макете есть отступы, как мне их сделать?

# Как мне писать текст с разными шрифтами?

# Как мне подключить компонент?

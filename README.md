WIP
ДЛЯ РАЗРАБОТЧИКОВ ПРИЛОЖЕНИЙ

[we](#goal)

# На чем мы пишем

-   Typescript
-   React
-   Redux
-   cssModules + postCSS

# Чем мы собираем
-   [yarn](https://yarnpkg.com/) для установки зависимостей
-   [arui-scripts](https://github.com/alfa-laboratory/arui-scripts) для проектов
-   [library-utils](https://github.com/alfa-laboratory/library-utils) или [rollup]() (пока концепт) для библиотек

# Чем тестим

-   jest
-   cypress

# Линтинг кода и форматирование

-   eslint
-   stylelint
-   commitlint
-   preеtier
-   [arui-presets-lint](https://github.com/alfa-laboratory/arui-presets-lint) Все настройки тут

# Библиотеки для конкретных задач

-   [date-fns](https://date-fns.org/) для работы с датами
-   [axios](https://github.com/axios/axios) для запросов на сервер. ВНИМАНИЕ!!! В приложении у вас должно быть минимум явного вызова axios. 99% случаев покроет [библиотекка шаремых сервисов](http://git.moscow.alfaintra.net/projects/RET/repos/retail-front-services/browse/src/api)
-   [lodash](https://lodash.com/) утилитарные функции общего назначения
-   [qrcode.react](https://github.com/zpao/qrcode.react) для генерации QR-кодов

# Какая структура должна быть в папке с компонентом, как называть файлы, типы, что экспортить?

Структура для папки с компонентами в проекте:

```
my-component/
  index.tsx
  index.module.css
  private-component/
    index.tsx
    index.module.css
```

# Где мне взять переменные для цветов?<a name="goal"><a/>

В библиотеке [core-components](https://github.com/alfa-laboratory/core-components).

[Файл с цветами](https://github.com/alfa-laboratory/core-components/blob/master/packages/vars/colors.css)

# Где мне взять иконки?

-   [git](https://github.com/alfa-laboratory/icons)
-   [figma](https://www.figma.com/file/QoGuPDB1hAMoMMqsQQ4Mx7lB/Icons?node-id=3882%3A144)

## Как подключить?

```
yarn add @alfalab/icons
```

импорт через PascalCase: `Имя-из-figma`+`Icon`

# Как мне называть классы для компонентов?

# Где мы храним частопереиспользуемые функции?

На текущий момент формируется это место [здесь](https://github.com/alfa-laboratory/tools)
Пока можно брать функции форматирования [отсюда](http://git.moscow.alfaintra.net/projects/EF/repos/arui-private/browse/src/lib/formatters.ts) (к примеру, `pluralize`)

# Как оттопырить data-test-id тестеровщику если очень надо?

# В моем макете есть отступы, как мне их сделать?

# Как мне писать текст с разными шрифтами?

# Как мне подключить компонент?

ДЛЯ РАЗРАБОТЧИКОВ БИБЛИОТЕКИ КОМПОНЕНТОВ (Это должно быть описано в библиотеке компонентов)

# Как импортировать компоненты из модулей, которые экспортируют много React-компонентов?

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

# Использование callback-функций в компонентах

```
// bad
return <Button onClick={() => setShowActions(!showActions)} />;

// good
const toggleActions = () => setShowActions(!showActions);

return <Button onClick={toggleActions} />;
```

# Что покрывать юнит тестами?

# Как писать документацию?

# Нужно оттопыривать data-test-id (как, мотивация)

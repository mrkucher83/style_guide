# Руководство по стилю
Этот документ определяет правила форматирования и стиля.
Он направлен на улучшение совместной работы, качество кода и создание вспомогательной инфраструктуры.

Полезные ссылки:
[Style Guide Vue.js](https://vuejs.org/v2/style-guide/#Priority-A-Essential)

***
- Каждый компонент должен находиться в своем собственном файле.
```
components/
|- TodoList.vue
|- TodoItem.vue
```
- Имена файлов должны быть в PascalCase.
```
components/
|- MyComponent.vue
```
- Базовые компоненты (чистые компоненты), должны начинаться
  с определенным префиксом, например **Base**, **App** или **V**.
```
components/
|- BaseButton.vue
|- BaseTable.vue
|- BaseIcon.vue
```
- Компоненты, которые должны иметь только один активный экземпляр, должны начинаться с префикса The.
```
components/
|- TheHeading.vue
|- TheSidebar.vue
```
- Дочерние компоненты, которые тесно связаны со своими родителями, должны включать имя родительского компонента в качестве префикса.
```
components/
|- TodoList.vue
|- TodoListItem.vue
|- TodoListItemButton.vue
```
- Имена компонентов должны начинаться со слов высшего уровня (часто наиболее общих) и заканчиваться описательными модифицирующими словами.
```
components/
|- SearchButtonClear.vue
|- SearchButtonRun.vue
|- SearchInputQuery.vue
|- SearchInputExcludeGlob.vue
|- SettingsCheckboxTerms.vue
|- SettingsCheckboxLaunchOnStartup.vue
```
- Предпочтительный порядок расположения блоков в `.vue` файле: template, потом script и далее style.
```vue
<template>
  <div class="Ranger__Wrapper">
    <!-- ... -->
  </div>
</template>

<script  lang="ts">
  export default {
    // обязательно не забываем имя компонента.
    name: 'RangeSlider',
    // можем использовать композицию уже существующих к.
    extends: {},
    // перечисление свойств и переменных
    props: {
      bar: {}, // еще лучше если по-алфавиту
      foo: {},
      fooBar: {},
    },
    data() {},
    computed: {},
    // когда внутри используются другие компоненты.
    components: {},
    // методы
    watch: {},
    methods: {},
    // методы жизненного цикла компонента.
    beforeCreate() {},
    mounted() {},
};
</script>

<style scoped lang="scss"></style>
```

- Имена компонентов всегда должны состоять из нескольких слов,
  за исключением корневых компонентов (App) и встроенных компонентов,
  предоставляемых Vue, таких, как `<transition>` или `<component>`.
```
export default {
  name: 'TodoItem',
  // ...
}
```

- Определения **props** должны быть как можно более подробными.
```vue
props: {
  status: {
    type: String,
    required: true
  }
}
```
- При объявлении в именах **props** всегда должен использоваться camelCase, а в шаблонах и JSX - kebab-case.
```js
props: {
  greetingText: String
}
```
```vue
<WelcomeMessage greeting-text="hi"/>
```
- Компонент **data** должен быть функцией.
```
export default {
  data () {
    return {
      foo: 'bar'
    }
  }
}
```
- Элементы с несколькими атрибутами должны занимать несколько строк, по одному атрибуту на строку.
```vue
<img
  src="https://vuejs.org/images/logo.png"
  alt="Vue Logo"
>
```
- Значения атрибутов HTML всегда должны заключаться в кавычки.
```vue
<AppSidebar :style="{ width: sidebarWidth + 'px' }" />
```
- Сокращения директив ( ':' для v-bind:, '@' для v-on: и '#' для v-slot) следует использовать всегда или никогда.
```vue
<input
  :value="newTodoText"
  :placeholder="newTodoInstructions"
  @input="onInput"
  @focus="onFocus"
>
```
- Всегда используйте `key` с `v-for`.
```html
<ul>
  <li
    v-for="todo in todos"
    :key="todo.id"
  >
    {{ todo.text }}
  </li>
</ul>
```
- Область видимости стиля компонента.
    - Используйте **scoped** атрибут
```scss
<!-- Using the scoped attribute -->

<style scoped lang="scss">
  .button {
    border: none;
    border-radius: 2px;
  }
</style>
``` 
- Используйте стратегию именования классов на основе методологии [БЭМ](https://ru.bem.info/methodology/).

```scss
<!-- Using the BEM convention -->

<style scoped lang="scss">
  .circle {
    fill: transparent;
    stroke: #ffffff;
    stroke-width: 1px;

    &__shadow {
       opacity: 0.3;
  
       animation: rotate 10s 0s linear alternate infinite;
     }
    }
</style>
```








# test

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

# HTML

## Синтаксис
* Для отступов у вложенных элементов используются два пробела.
* Теги и их атрибуты пишутся строчными буквами.
* Для значений атрибутов используются двойные кавычки.
* У одиночных тегов не ставится `/` (<del>`<img />`</del>, <del>`<br />`</del>).
* Необязательные закрывающие теги не опускаются (`</li>`, `</body>`).

## Валидность
Документ должен проходить [проверку валидатором](http://validator.w3.org/nu/).

## Семантичность
Документ должен быть семантичным, с использованием подходящих тегов, таких как `<main>`, `<header>`, `<aside>` и др.
* Параграфы текста располагаются в `<p>`, а не делятся при помощи нескольких `<br>`.
* Списки размечаются при помощи `<ul>`, `<ol>`, `<dl>`, а не `<div>` или `<p>`.
* И т. д.

## Doctype
В начале страницы должен быть указан актуальный `doctype`.
```
<!DOCTYPE html>
```

## Атрибут языка
Для элемента `<html>` в атрибуте `lang` должен указываться соответствующий язык документа.
```
<html lang="ru">
```

## Кодировка
Кодировка символов должна быть явно указана.
```
<meta charset="utf-8">
```

## Подключение стилей
Стилевые файлы подключаются внутри `<head>` при помощи `<link>`, при этом атрибут `type` не указывается.
```
<html lang="ru">
  <head>
    <link rel="stylesheet" href="style.css">
```

## Подключение скриптов
Скрипты подключаются внизу страницы, при этом атрибут `type` не указывается.
```
    <script src="script.js"></script>
  </body>
</html>
```

## Порядок атрибутов
* `class`
* `id`, `name`
* `data-*`
* `src`, `for`, `type`, `href`, `value`
* `title`, `alt`
* `role`, `aria-*`
У одинаковых элементов порядок атрибутов должен быть единообразным.

## Логические атрибуты
Для логических атрибутов значение не указывается, а сами атрибуты указываются последними и в единообразной последовательности.
```
<input type="checkbox" required checked>
```

## Подписи полей ввода
Элемент формы связывается с его описанием при помощи атрибута `for`.

## Размеры изображений
Элементам `<img>` следует явно задавать размеры при помощи атрибутов. Если размер задаётся в пикселях, размерность не нужна.

По возможности изображениям указываются действительные размеры.


## Сокращение разметки
По возможности следует избегать излишних родительских элементов.
```
<!-- not so great -->
<span class="avatar">
  <img src="photo.jpg">
</span>

<!-- better -->
<img class="avatar" src="photo.jpg">
```


# CSS

## Синтаксис
* Для отступов внутри правил используются два пробела.
* После значения свойства ставится точка с запятой.
* Названия тегов, свойств и их значений пишутся строчными буквами.
* Не ставится пробел после запятых в `rgba()`, `hsla()` и др.
* Во всех случаях в стилях используются двойные кавычки.
* После двоеточия ставится один пробел.
* До и после комбинатора между селекторами ставится пробел.
* Каждое объявление в правиле пишется на новой строке.
* Перед открывающейся фигурной скобкой ставится один пробел. После скобки запись идёт с новой строки.
* Закрывающая фигурная скобка пишется на новой строке, без отступа. Следующее после этого правило отделяется пустой строкой.
* Единицы измерения не пишутся там, где в них нет необходимости.
* Начальный ноль опускается: `.5` вместо `0.5`.
* Hex-коды сокращаются: `#fff` вместо `#ffffff`.

## Имена классов
Для написания классов используются английские слова и термины. Имена классов должны быть такими, чтобы по ним можно было быстро понять, какому элементу страницы задан класс.

## Подключение стилей
Стили лучше подключать при помощи `<link>`, нежели используя `@import`.

## Шрифты
После основного шрифта указываются альтернативные [веб-безопасные шрифты](//cssfontstack.com) и тип семейства.

## Медиа-выражения
Медиа-выражения располагаются максимально близко к соответствующим правилам. Не стоит их выносить в отдельный файл или помещать вниз документа.

## Префиксы
Для CSS-свойств с префиксом указан его вариант без префикса, и это указание идёт последним.

Используются только [необходимые вендорные префиксы](//shouldiprefix.com).

Выравнивание данных свойств осуществляется по значению.
```
.selector {
  -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
          box-shadow: 0 1px 2px rgba(0,0,0,.15);
}
```

## Одиночные объявления
К большим группам правил, состоящих из одного свойства, может применяться запись в одну строку. В этом случае следует ставить пробел после открывающей и перед закрывающей скобками.
```
.span1 { width: 60px; }
.span2 { width: 140px; }
.span3 { width: 220px; }

.icon           { background-position: 0 0; }
.icon-home      { background-position: 0 -20px; }
.icon-account   { background-position: 0 -40px; }
```

## Значения из нескольких свойств
После разделительной запятой ставится пробел. Длинные значения свойств могут быть помещены на отдельной строке каждое.
```
.selector {
  box-shadow:
    1px 1px 1px #000,
    2px 2px 1px 1px #ccc inset;
  background-image:
    linear-gradient(#fff, #ccc),
    linear-gradient(#f3c, #4ec);
}
```

## Сокращённые нотации
Не стоит использовать сокращённые объявления, в которых есть необходимый набор свойств, часть из которых излишне переопределяется.
```
/* not so great */
.element {
  margin: 0 0 10px;
  border-radius: 3px 0 0 0;
}

/* better */
.element {
  margin-bottom: 10px;
  border-top-left-radius: 3px;
}
```

С другой стороны, свойства следует можно объединять, если можно избежать переопределения.
```
/* not so great */
.element {
  border-width: 1px;
  border-style: solid;
  border-color: #000;
  background-color: #000;
  background-image: url(images/bg.gif);
  background-repeat: no-repeat;
  background-position: top right;
}

/* better */
.element {
  border: 1px solid #000;
  background: #000 url(images/bg.gif) no-repeat top right;
}
```

## Вложенность селекторов
Вложенность селекторов не больше двух. Псевдоэлементы и псевдоклассы не увеличивают уровень вложенности.

## Методология
Используется [БЭМ](//ru.bem.info/methodology/css/).

## Комментарии
Стили комментариев должны быть простыми и однородными для всего проекта.
* Комментарий помещается на строке перед комментируемым фрагментом кода.
* Следует избегать добавления комментариев в конец строки.
* Комментарии используются для оформления разделов внутри файла.

```
/* ==========================================================================
   Блок комментариев для раздела
   ========================================================================== */

/* Блок комментариев для подраздела
   ========================================================================== */

/*
 * Блок комментариев для группы правил.
 * Хорошо подходит для подробных пояснений и документации.
 */

/* Обычный комментарий */
```

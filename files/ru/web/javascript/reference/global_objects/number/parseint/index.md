---
title: Number.parseInt()
slug: Web/JavaScript/Reference/Global_Objects/Number/parseInt
tags:
  - ECMAScript6
  - JavaScript
  - Method
  - Number
translation_of: Web/JavaScript/Reference/Global_Objects/Number/parseInt
---
{{JSRef("Global_Objects", "Number")}}

## Сводка

Метод **`Number.parseInt()`** разбирает строковый аргумент и возвращает целое число. Этот метод ведёт себя идентично глобальной функции {{jsxref("Global_Objects/parseInt", "parseInt()")}} и является частью ECMAScript 6 (его целью является модуляризация глобальных сущностей).

## Синтаксис

```
Number.parseInt(string[, radix])
```

### Параметры

- `string`
  - : Значение для разбора. Если параметр не является строкой, он будет в неё преобразован. Ведущие пробельные символы в строке игнорируются.
- `radix`
  - : Необязательный параметр. Целое число, представляющее основание системы счисления для числа в указанной выше строке. Для избежания непонятностей при чтении кода и гарантии предсказуемого поведения **всегда определяйте этот параметр**. Различные реализации дадут разные результаты, если основание системы счисления не будет указано.

### Возвращаемое значение

Целое число, полученное парсингом (разбором и интерпретацией) переданной строки. Если первый символ строки не может быть преобразован в число, то возвращается [`NaN`](/ru/docs/Web/JavaScript/Reference/Global_Objects/NaN).

## Описание

Этот метод имеет ту же функциональность, что и глобальная функция {{jsxref("parseInt", "parseInt()")}}:

```js
Number.parseInt === parseInt; // true
```

Пожалуйста, обратитесь к документации по глобальной функции {{jsxref("Global_Objects/parseInt", "parseInt()")}} для просмотра подробного описания и примеров.

## Полифил

```js
if (Number.parseInt === undefined) {
    Number.parseInt = window.parseInt;
}
```

## Спецификации

{{Specifications}}

## Совместимость с браузерами

{{Compat}}

## Смотрите также

- Объект {{jsxref("Global_Objects/Number", "Number")}}, которому принадлежит этот метод.
- Глобальная функция {{jsxref("Global_Objects/parseInt", "parseInt()")}}.

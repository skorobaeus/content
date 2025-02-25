---
title: "`FinalizationRegistry`"
description: "Объект, который позволяет регистрировать обработчики сборки мусора на зарегистрированных в нём объектах."
authors:
  - doka-dog
related:
  - js/collection-weakmap
  - js/map
  - js/set
tags:
  - doka
  - placeholder
---

## Кратко

Объект, который управляет обработчиками событий, которые срабатывают, когда сборщик мусора собирает зарегистрированные в нём объекты. Это своеобразный реестр, в котором хранится всё, что нужно сделать с объектами перед их сборкой.

Колбэк очистки (cleanup callback) ещё называют финализатором (finalizer). Это такая функция, которая выполняется, когда зарегистрированный объект собирается сборщиком мусора.

## Пример

Создаём регистр с колбэком `heldValue`:

```js
const registry = new FinalizationRegistry((heldValue) => {
  // …
})
```

## Как пишется

Чтобы создать `FinalizationRegistry`, обязательно используйте оператор `new`. В скобках в качестве аргумента указывают колбэк очистки.

```js
new FinalizationRegistry(anyCallbackFunction)
```

Старайтесь не полагаться на обработчики событий в объекте `FinalizationRegistry`. Сборка мусора — сложный процесс, и никто не знает, когда эти колбэки сработают и сработают ли вообще.

## Методы

- `.register()` — регистрирует объект в реестре.
- `.unregister()` — отменяет регистрацию объекта в реестре.

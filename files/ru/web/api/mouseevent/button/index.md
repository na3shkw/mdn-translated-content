---
title: MouseEvent.button
slug: Web/API/MouseEvent/button
---

{{APIRef("UI Events")}}

**`MouseEvent.button`** свойство доступное только для чтения, возвращает значение, соответствующее нажатой кнопки мыши, которое инициировало событие.

Это свойство предоставляет информацию только о том, какая кнопка или несколько кнопок были нажаты или отпущены для инициации события, и не имеет отношения к таким событиям как [`mouseenter`](/ru/docs/Web/API/Element/mouseenter_event), [`mouseleave`](/ru/docs/Web/API/Element/mouseleave_event), [`mouseover`](/ru/docs/Web/API/Element/mouseover_event), [`mouseout`](/ru/docs/Web/API/Element/mouseout_event) или [`mousemove`](/ru/docs/Web/API/Element/mousemove_event).

Пользователь может изменять конфигурацию кнопок своей мыши таким образом, что значение ноль будет получено при нажатии кнопки, не являющейся физически крайней левой кнопкой мыши, тем не менее, событие будет вести себя так, как будто левая кнопка была нажата в стандартной раскладкой кнопок.

> [!NOTE]
> Не путайте это свойство со свойством {{domxref ( "MouseEvent.buttons")}}, которое содержит значения, соответствующие нажатым кнопкам мыши для всех типов событий мыши.

## Синтаксис

```
var buttonPressed = instanceOfMouseEvent.button
```

### Возвращаемые значения

Число, соответствующее нажатой кнопке:

- `0`: Нажата основная кнопка. Левая кнопка мыши или переназначенная пользователем другая кнопка
- `1`: Нажата вспомогательная кнопка. Колёсико или средняя кнопка мыши, если она есть
- `2`: Нажата вторичная кнопка. Правая кнопка мыши
- `3`: Нажата четвёртая кнопка мыши. Обычно кнопка браузера _Назад_
- `4`: Нажата пятая кнопка мыши. Обычно кнопка браузера _Вперёд_

Для мыши, перенастроенной под левую руку, значения нажатых кнопок меняются местами. В этом случае значения читаются справа налево.

## Пример

```js
<script>
var whichButton = function (e) {
    // Handle different event models
    var e = e || window.event;
    var btnCode;

    if ('object' === typeof e) {
        btnCode = e.button;

        switch (btnCode) {
            case 0:
                console.log('Нажата левая кнопка.');
            break;

            case 1:
                console.log('Нажата средняя кнопка или колёсико.');
            break;

            case 2:
                console.log('Нажата правая кнопка.');
            break;

            default:
                console.log('Неопределённое событие: ' + btnCode);
        }
    }
}
</script>

<button onmouseup="whichButton(event);" oncontextmenu="event.preventDefault();">Нажмите кнопку мыши...</button>
```

## Спецификации

{{Specifications}}

## Совместимость с браузерами

{{Compat}}

## Смотрите также

- {{domxref('"MouseEvent"')}}

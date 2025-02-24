---
title: WindowTimers.clearInterval()
slug: Web/API/clearInterval
translation_of: Web/API/WindowOrWorkerGlobalScope/clearInterval
original_slug: Web/API/WindowOrWorkerGlobalScope/clearInterval
---
{{APIRef("HTML DOM")}}

Cancela una acción reiterativa que se inició mediante una llamada a {{domxref("window.setInterval", "setInterval")}}.

## Sintaxis

```
window.clearInterval(intervalID)
```

`intervalID` es el identificador de la acción reiterativa que se desea cancelar. Este ID se obtiene a partir de `setInterval()`.

## Ejemplo

Vea el [ejemplo de`setInterval()`](/es/docs/DOM/window.setInterval#Example).

## Especificación

| {{SpecName('HTML WHATWG', 'timers.html#timers', 'clearInterval')}} | {{Spec2('HTML WHATWG')}} |
| ---------------------------------------------------------------------------------------- | -------------------------------- |

## Vea también

- [JavaScript timers](/es/docs/JavaScript/Timers)
- {{domxref("WindowTimers.setTimeout")}}
- {{domxref("WindowTimers.setInterval")}}
- {{domxref("WindowTimers.clearTimeout")}}
- {{domxref("window.requestAnimationFrame")}}
- [_Daemons_ management](/es/docs/JavaScript/Timers/Daemons)

Сводка
Метод trim() удаляет пробельные символы с начала и конца строки. Пробельными символами в этом контексте считаются все собственно пробельные символы (пробел, табуляция, неразрывный пробел и прочие) и все символы конца строки (LF, CR и прочие).

Синтаксис
```
str.trim()
```

Описание
Метод trim() возвращает строку с вырезанными пробельными символами с её концов. Метод trim() не изменяет значение самой строки.

Полифил
Запуск следующего кода до любого другого создаст метод trim(), если он ещё не реализуется браузером.

```
if (!String.prototype.trim) {
  (function() {
    // Вырезаем BOM и неразрывный пробел
    String.prototype.trim = function() {
      return this.replace(/^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g, '');
    };
  })();
}
```

#Stringprototype
#js
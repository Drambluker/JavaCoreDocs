# Введение в язык Java

Java — строго типизированный объектно-ориентированный язык программирования общего назначения, разработанный компанией Sun Microsystems (в последующем приобретённой компанией Oracle).

Приложения Java обычно компилируются в специальный байт-код, поэтому они могут работать на любой компьютерной архитектуре, для которой существует реализация виртуальной Java-машины.

## Применение языка Java

Java может использоваться для целого ряда задач: от создания десктопных приложений до написания крупных веб-порталов и сервисов. Кроме того, язык Java активно применяется для создания программного обеспечения для множества устройств: обычных ПК, планшетов, смартфонов и мобильных телефонов и даже бытовой техники. Достаточно вспомнить популярность мобильной ОС Android, большинство программ для которой пишутся именно на Java.

## Ключевые особенности Java

### Простота

Java является языком с Си-подобным синтаксисом и близок в этом отношении к C/C++ и C#.

Другой аспект простоты - краткость. Программы, написанные на языке программирования Java занимают немного места. Так, например, размер основного интерпретатора составляет около 40 Кбайт, а стандартные библиотеки занимают ещё 175 Кбайт (?).

Еще одной ключевой особенностью языка Java является то, что он поддерживает автоматическую сборку мусора. А это значит, что не надо освобождать вручную память от ранее использовавшихся объектов, как в С++, так как сборщик мусора это сделает автоматически. (?)

### Объектно-ориентированность

Java является объектно-ориентированным языком. Он поддерживает полиморфизм, наследование, статическую типизацию. Объектно-ориентированный подход позволяет решить задачи по построению крупных, но в тоже время гибких, масштабируемых и расширяемых приложений.

### Распределенность

Язык Java предоставляет разработчику обширную библиотеку программ для передачи данных в сети интернет по протоколу TCP/IP, НТТР и FTP. Приложения на Java способны открывать объекты и получать к ним доступ по сети с такой же легкостью, как и в локальной файловой системе.

### Надежность

Язык Java предназначен для написания программ, которые должны надежно работать в любых условиях. Основное внимание в этом языке уделяется раннему обнаружению возможных ошибок, контролю в процессе выполнения программы, а так же устранению ситуации, которые могут вызвать ошибки... Единственное существенное отличие языка Java от С++ кроется в модели указателей, принятой в Java, которая исключает возможность записи в произвольно выбранную область памяти и повреждения данных.

### Безопасность

Java позволяет создавать системы, защищенные от вирусов и несанкционированного доступа. Ниже перечислены некоторые виды нарушения защиты, которые с самого начала предотвращает система безопасности Java.

- Намеренное переполнение стека выполняемой программы - один из распространенных способов нарушения защиты, используемых вирусами.
- Повреждение данных на участках памяти, находящихся за пределами пространства, выделенного процессу.
- Несанкционированное чтение файлов и их модификация.

### Независимость от архитектуры компьютера

Компилятор генерирует объектный файл, формат которого не зависит от архитектуры компьютера. Скомпилированная программа может выполняться на любых процессорах, а для её работы требуется лишь исполняющая система Java. Код, генерируемый компилятором Java, называется байт-кодом. Он разработан таким образом, чтобы его можно было .легко интерпретировать на любой машине или оперативно преобразовать в собственный машинный код.

### Переносимость

В отличие от С и С++, ни один из аспектов спецификации Java не зависит от реализации компьютера. Разрядность примитивных типов данных и арифметические операции над ними строго определены.

### Интерпретируемость

Байт-код, который компилируется из исходных кодов Java, на самом деле не компилируется, и интерпретируется, т.е. переводится в машинный код во время выполнения программы, а не на этапе сборки приложения.

### Производительность

Интерпретируемый байт-код имеет достаточную производительность, но бывают ситуации, когда требуется еще более высокая производительность. Так, например, динамический компилятор Java может отслеживать код, который выполняется чаще, и оптимизировать по быстродействию только эту часть кода.

### Многопоточность

Java один из первых языков программирования, где поддержали параллельное программирование. Хотя параллельное программирование никогда не было простым занятием, в Java сделано немало, чтобы этот процесс стал более управляемым.

### Динамичность

В Java-библиотеки можно свободно включать новые методы и объекты, ни коим образом не затрагивая приложения, использующие эти библиотеки.

---

## Дополнительные материалы

- [Java - Википедия](https://ru.wikipedia.org/wiki/Java)
- [Java (программная платформа) - Википедия](https://ru.wikipedia.org/wiki/Java_\(программная_платформа\))

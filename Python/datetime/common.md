# Модули `time` и `datetime`

Модуль `time` предназначен для работы с так называемым _unix-временем_ (unix timestamps) - системой описания моментов во времени, которая была принята в операционной системе _Unix_. Момент во времени определяется как целое число - количество секунд, прошедших с полуночи (00:00:00) 1 января 1970 года.

Пример получения текущего момента времени:
```python
import time
curr_time = time.time()
print(curr_time)
```
Результат:
```python
>>> 1654513868.6584458
```
Результатом является число (объект класса `float`), содержит количество секунд и микросекунд. Оно может быть при необходимости преобразовано в целое число (с отбрасыванием микросекунд):
```python
print(int(curr_time))
>>> 1654513868
```
Это значение может быть записано в файл, в базу данных и т.д. В любой момент мы можем "извлечь" дату в виде строки. Для этого используем метод `fromtimestamp` из модуля `datetime`
```python
from datetime import datetime
t = datetime.fromtimestamp(1654513868)
```
Объект, полученный в переменной `t`, является экземпляром класса `datetime`. Строку, содержащую значения года, месяца, дня и т.д. мы можем получить, используя метод `strftime` этого объекта:
```python
t.strftime("%Y.%d.%m %H:%M:%S")
>>> '2022.06.06 14:11:08'
```
В качестве аргумента, метод `strftime` принимает строку, содержащую специальные коды (англ. `format codes` или `directives`)
```
%Y - год в 4-х значном формате
%d - день
%m - номер месяца
%H - часы в 24-м формате
%M - минуты
%S - секунды
```
[Полный список кодов](https://docs.python.org/3.2/library/datetime.html#strftime-and-strptime-behavior)

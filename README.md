Abstract
========

Механические слоты — игровые автоматы с рычагом для запуска вращения барабанов (обычно их 3)
Выигрыш определяется комбинацией символов на барабанах. 
Большинству комбинаций соответствуют небольшие выигрыши
Наиболее редким - значительные суммы.

Существуют также особые комбинации, запускающие дополнительную (или - **бонус**) игру.
Одной из разновидностей таких игр является **big-cash**. См. видео:

<a href="http://www.youtube.com/watch?feature=player_embedded&v=tWojSuoJaYQ&t=45s
" target="_blank"><img src="http://img.youtube.com/vi/tWojSuoJaYQ/0.jpg" 
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>

В качестве тестового задания предлагается написать рабочий прототип игры **big-cash**.
При этом предполагается, что кандидат:
* В полной мере владеет шаблонами проектирования
* В состоянии писать self-documenting code
* Понимает клиент-серверную архитектуру
* Способен работать с sql / nosql storage
* Имеет опыт с concurrency

Постановка задачи
=================

1. Задается набор пачек купюр, например, следующей стоимостью:
   25, 25, 50, 50, 100, 250, 500, 1000, 5000
2. Из заранее заданного набора пачек купюр машина делает 4 последовательных оффера игроку.
   В каждом оффере, формируемом случайным образом может оказаться от 1 до 3 пачек. 
   Сумма потенциального выигрыша складывается из номинала пачек.
  * 25 + 50
  * 500
  * 100 + 25 + 25
  * 25 + 25
3. Игрок может отказаться до трех раз от оффера. 
   В этом случае игрок собирает результат четвертого оффера (25 + 25 - всего 50 кредитов)
   
   
Требования к решению
====================

1. Написать прототип игрового сервера. Функционал:
  * Подключение игрока (tcp).
  * Выдача информации о содержимом пачек для игры.
  * Выдача До 4-х последовательных офферов.
  * Начисление "выигранной" суммы на счет игроку.
2. Написать прототип бота (клиента) игры. Функционал:
  * Подключение к серверу.
  * Ответ да/нет на предложение от сервера.
  * Отключение после начисления выигрыша.
3. Результат игры записывать в Sql / Nosql storage
4. Придерживаться стека технологий: scala/akka/sbt + netty
5. Результат оформить в виде запускаемого из sbt проекта на github

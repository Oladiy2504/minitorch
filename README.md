# minitorch
The full minitorch student suite. 


To access the autograder: 

* Module 0: https://classroom.github.com/a/qDYKZff9
* Module 1: https://classroom.github.com/a/6TiImUiy
* Module 2: https://classroom.github.com/a/0ZHJeTA0
* Module 3: https://classroom.github.com/a/U5CMJec1
* Module 4: https://classroom.github.com/a/04QA6HZK
* Quizzes: https://classroom.github.com/a/bGcGc12k


## Module 1: обучение моделей

Мне было довольно лениво самому описывать результаты запусков, поэтому я использовал GPT-6 Astra (агент Codex) для прогона запусков и составления этого README. 

Все логи агент аккуратно поместил в папку artifacts/task1_5/logs. Результат работы агента вы можете наблюдать здесь, а промт был следующий:
"Ознакомься с репозиторием учебного проекта. Мне необходимо запустить project/run_scalar.py с различными конфигурациями *тут были описаны конфигурации* и осуществить логирование результатов + добавить информацию об этом в README.md. Прогони необходимые запуски, во всех запусках используй одинаковый random seed. Не изменяй код проекта."

В столбцах эпох указаны **суммарный loss / число верных ответов из 50**.
Это стандартные логи до шага SGD; итоговая точность пересчитана после последнего обновления весов на обучающих данных.

| Датасет | Эпоха 10 | Эпоха 100 | Эпоха 500 | Итоговая точность | Полный лог |
|---|---:|---:|---:|---:|---|
| Simple | 14.827 / 50 | 0.513 / 50 | 0.063 / 50 | 50/50 (100%) | [simple](artifacts/task1_5/logs/simple-h10-lr0.5-seed42.log) |
| Diag | 18.605 / 40 | 5.905 / 46 | 3.414 / 47 | 48/50 (96%) | [diag](artifacts/task1_5/logs/diag-h10-lr0.5-seed42.log) |
| Split | 32.603 / 36 | 16.541 / 46 | 5.791 / 48 | 50/50 (100%) | [split](artifacts/task1_5/logs/split-h10-lr0.5-seed42.log) |
| Xor | 31.403 / 32 | 15.576 / 43 | 0.432 / 50 | 50/50 (100%) | [xor](artifacts/task1_5/logs/xor-h10-lr0.5-seed42.log) |

Во всех четырёх запусках loss снизился между указанными эпохами. Полные логи содержат настройки, вывод каждые 10 эпох и итоговую оценку.

Начальные опыты с `HIDDEN=2` при том же seed остановились на 27/50 для [Simple](artifacts/task1_5/logs/simple-h2-lr0.5-seed42.log) и 40/50 для [Diag](artifacts/task1_5/logs/diag-h2-lr0.5-seed42.log), поэтому ширина была увеличена до 10. Эти логи также сохранены.

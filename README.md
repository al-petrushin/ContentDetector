# ContentDetector


Detect hard/soft skills from resumes in Russian.

Это — модуль, который из текста резюме/вакансии вычленяет профессиональные навыки (например, 1C, .NET) и "мягкие" навыки (обучаемость, коммуникабельность и т. п.).

**Наиболее оптимальный сценарий использования** этого модуля заключается в том, чтобы произвести анализ созданной вакансии/резюме и предложить пользователю (как работнику, так и работодателю) набор выявленных навыков, из которого тот уберёт на свой взгляд лишние.

# Как этим пользоваться

Основная функция модуля — это ```get_content_from_text``` из файла [detector.py](https://github.com/PasaOpasen/ContentDetector/blob/master/content_detector/detector.py). Она принимает на вход список из строк резюме и возвращает список навыков (каждый навык — это просто строка).

```python
lines = ['Программист сайтов Битрикс и Битрикс 24.',
             'Партнёр Битрикс и Битрикс 24, интеграция Битрикс 24.',
             'Создание и продвижение сайтов, интернет магазина, лендинга.',
             'Дизайн, верстка, интернет маркетинг. Seo, топ 10, директ, соц сети.',
             'Так же работаю с любыми другими движками сайтов.',
             'Парсинг сайтов.','Стаж более 15 лет на фрилансе.']
    
print(get_content_from_text(lines))
# ['дизайн', 'дизайн сайтов', 'рекламные сервисы', 'разработка сайтов', 'верстка сайтов', 'оптимизация сайтов', 'Битрикс']
    
lines = ['Профессиональный опыт в сфере IT 10 лет.',
         'Опыт работы и поддержки информационных систем (сервисов) в крупных компаниях, предприятиях и гос. учреждениях.',
         '"KSB" "Россконгресс" "Burger King" "KFC"',
         'Высокая обучаемость.',
         'Грамотная речь, умение вести переговоры.',
         'Знание Английского языка: базовые знания.',
         'Управление персоналом, распределение задач.',
         'Умение самостоятельно проводить анализ и выявлять причины возникновения ошибок, и проблем.',
         'Коммуникабелен, стрессоустойчив. Без вредных привычек.']
    
 print(get_content_from_text(lines))
 # ['информационные системы', 'английский', 'грамотность', 'дружелюбность', 'организованность', 'обучаемость', 
 #'стрессоустойчивость', 'коммуникабельность', 'лидерские качества', 'умение убеждать', 'Burger King', 'KFC', 'KSB']   
    
 lines = ['Студент Тольяттинской Академии управления',
          'В данный момент нахожусь на дистанционной форме обучения, поэтому ищу работу с графиком полной рабочей загруженности.',
          'Имею четкую профессиональную траекторию и всегда ответственно подхожу к выполнению возложенных на меня задач.']
    
 print(get_content_from_text(lines))
 #['обучаемость', 'лидерские качества', 'ответственность']
 
```

Функция имеет необязательный аргумент ```use_wiki = True```. Его назначение в том, чтобы активировать/дезативировать поиск неизвестных основному алгоритму понятий с помощью [**wikipedia API**](https://github.com/goldsmith/Wikipedia). Это имеет смысл, если резюме/вакансия изобилует IT-терминами, однако поиск поиск может занять несколько секунд.

# Как это работает


## Преобразование текста в набор n-gramm

## Алгоритм на основе графов

## Запасной алгоритм





# Architectural Ката 2024

Проектный конкурс для архитекторов от МТС

## Архитектурное решение USuperTravel

[USuperTravel](./docs/index.md)

# 1. Условия участия

**Артефактом участия** в конкурсе является зарегистрированное решение кейса от команды. Присылайте свои решения в формате презентации Power Point с предложенным решением кейса.
 
Вы можете участвовать один или собрать команду до 5 человек – в презентации на первом слайде нужно перечислить:
 - Название команды
 - Состав команды (ФИО, телеграмм аккаунты и телефонные номера)
 - Разложить детально свое решение кейса (в соответствии с критериями оценки)
 
Механика отбора команд будет вестись по выставлению максимального количества баллов. При одинаковом количестве баллов будут учитываться опциональные артефакты.
 
Презентация Power Point должна содержать основные артефакты (макс 80 баллов):
- Общее описание решения
- Диаграммы С4 контекстная (draw.io)
- Диаграммы С4 контейнерная (draw.io)
- Техстек
  
\+ дополнительные артефакты (макс 20 баллов):
- Состав команд для разработки решения (опционально)
- RoadMap (опционально)
- ADRs (опционально)
 
Далее жюри отбирают 10 лучших команд и приглашают на офлайн защиту проектов перед комиссией жюри на площадке проведения конференции.

Финалистам на открытие конференции будет предложено дополнительное задание, на подготовку которого будет выделено 4 часа во время проведения докладов. С собой необходимо принести ноутбуки и флешку.

# 2. mini ArchKata case USuperTravel

## 2.1. Описание
 
**USuperTravel** - это онлайн агрегатор предложений билетов на самолет, отелей, аренды автомобилей, а так же туров и других активностей. Оформление и продажа услуг происходит на ресурсе оператора услуги.

## 2.2. Необходимое решение

В стратегии компании выход на международные рынки с возможности масштабирования и снижение затрат на инфраструктуру.

Компания хочет перенести текущее решение on-premises в облачную инфраструктуру. 

Необходимо осуществить перенос в течении 6 месяцев.

## 2.3. Текущее решение

Текущая система представляет собой монолит, содержащий в себе логику взаимодействия с внешними системами партнеров для сбора информации об услугах и ценах. Дополнительно, 
система содержит функционал перенаправления пользователей на внешние сайты/ моб приложения партнеров.

Пользовательский интерфейс существует в веб-версии и моб приложении.

Текущее решение расположено на bare-metal в нескольких дата-центрах, поддерживаемых внутренним операционным департаментом. 

## 2.4. Требования

### 2.4.1. Функциональные требования

Необходимо улучшить подбор предложений на основании диалога ИИ с клиентом

### 2.4.2. Нефункциональные требования

|Атрибуты качества (Quality attribute)|Сценарии|Приоритет|
|--|--------|-|
|Доступность (Availability)|Портал может быть недоступен до 8 часов в процессе миграции. Критичные сервисы должны быть доступны 99.95% времени.|Высокий|
|Производительность (Performance)|С момента запуска поискового запроса до момента предоставления результатов не более 5 секунд. Пользовательская нагрузка: 1000 запросов в секунду|Средний|
|Масштабирование (Scalability)|Система должна поддерживать увеличение количества пользователей и единовременной нагрузки на систему при развитии бизнеса.|Средний|
|Безопасность (Security)|Защита от внешних атак и защищенные взаимодействия с системами партнеров |Высокий|

### 2.4.3. Опросник

|||
|-|-|
|Подтвердите или опровергните, что USuperTravel не поддерживает пользовательские профили|На данный момент не поддерживает, в будущем возможно добавить этот функционал|
|Должна ли быть legacy система отключена сразу после завершения миграции?|Первое время legacy система может работать в параллель для переключения на нее в случае проблем.|
|Должна ли система сохранять/логировать данные для дальнейшего анализа?|В данный момент функционал не поддерживается. Вы можете предложить свое решение для реализации данного функционала.|
|Какую БД (или комбинацию БД) использует сервис сейчас? Для каких целей?|PostgreSQL|
|Какой объем информации хранит эта БД (GB/TB) ?|1000 GB, выполняется резервное копирование данных|
|Партнеры предоставляют унифицированный API или все они различны?|Все они различны|
|Представлена ли система кэширования информации о перелетах в текущем решении?|В данный момент функционал не поддерживается. Вы можете предложить свое решение для реализации данного функционала.|

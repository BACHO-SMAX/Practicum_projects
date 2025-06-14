# Прогноз оттока клиентов для оператора «ТелеДом»

## Описание проекта
Оператор связи «ТелеДом» стремится снизить отток клиентов, предлагая им специальные условия до расторжения договора. 
Для этого необходима модель, способная предсказать вероятность ухода клиента на основе его персональных данных, истории обслуживания и характеристик договора.

Цель проекта — обучить модель классификации, определяющую, уйдёт ли клиент от оператора.

## Данные
В распоряжении команды находятся следующие файлы:
- `contract_new.csv` — параметры договора;
- `personal_new.csv` — персональные характеристики клиента;
- `internet_new.csv` — подключённые интернет-услуги;
- `phone_new.csv` — сведения об услугах телефонии.

Ключевое поле во всех таблицах — `customerID`. Целевой признак: факт расторжения договора (по дате `EndDate`).

## Структура репозитория
```
Practicum_projects/
│
├── TELEDOOM-git.ipynb          # Jupyter-ноутбук с проектом
├── contract_new.csv            # Договоры
├── personal_new.csv            # Персональные данные
├── internet_new.csv            # Интернет-услуги
├── phone_new.csv               # Услуги телефонии
└── README.md                   # Этот файл
```

## Используемые библиотеки
- `pandas`, `numpy` — анализ и обработка данных
- `matplotlib`, `seaborn` — визуализация
- `scikit-learn` — модели, метрики, препроцессинг
- `LightGBM`, `CatBoost` — градиентный бустинг

## Этапы проекта
1. **Загрузка и осмотр данных**:
   - Проверка типов, дубликатов, пропусков, соответствие форматов.

2. **Исследовательский анализ**:
   - Изучение распределений, визуализация зависимостей, анализ оттока по группам признаков.

3. **Объединение таблиц**:
   - Слияние всех датасетов в один датафрейм по `customerID`.

4. **Предобработка**:
   - Преобразование дат, создание бинарного целевого признака, кодирование категориальных данных.
   - Масштабирование числовых признаков.

5. **Обучение моделей**:
   - Протестированы модели: Logistic Regression, Random Forest, CatBoost, LightGBM.
   - Гиперпараметры подобраны через `GridSearchCV`.

6. **Оценка результатов**:
   - Метрики: `accuracy`, `precision`, `recall`, `f1`, `ROC-AUC`.
   - Лучшая модель достигла ROC-AUC > 0.88 на тесте.

## Выводы
- Отток клиентов можно прогнозировать с высокой точностью.
- Среди ключевых факторов: способ оплаты, длительность договора, подключенные интернет-услуги и наличие технической поддержки.
- Бизнесу стоит использовать модель для раннего выявления клиентов с высоким риском оттока и предложений специальных условий.

## Результаты
Модель готова к внедрению в систему CRM оператора. Она может помочь снизить отток и повысить лояльность клиентов за счёт персонализированных предложений.

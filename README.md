# 📊 Ecommerce Sales & Delivery Analysis – Power BI Report

Этот проект представляет собой визуальный отчет в Power BI, созданный для анализа работы онлайн-магазина. В нем рассматриваются ключевые бизнес-показатели, связанные с продажами, клиентами, товарами, доставкой и финансовыми результатами.

## 📁 Структура проекта

Ecommerce-Report/
├── Ecommerce_Sales_Analysis.pbix # Файл Power BI
├── README.md # Описание проекта
└── data/ # Исходные данные в CSV
├── orders.csv
├── products.csv
├── customers.csv
├── logistics.csv
└── payments.csv

## 🧠 Цели проекта

- Отслеживание объема продаж и доходов
- Анализ клиентской базы и повторных заказов
- Выявление популярных товаров и категорий
- Оценка сроков и качества доставки
- Выявление задержек и эффективности логистики

## 📌 Использованные страницы отчета

### 1. **Обзор**
- Общий доход, кол-во заказов, средний чек
- Доход по месяцам и категориям товаров
- Карта заказов по странам

### 2. **Товары и клиенты**
- Топ-10 продаваемых товаров
- Частота повторных покупок
- Заказы по регионам и сегментам клиентов

### 3. **Доставка и финансы**
- Среднее время доставки
- Количество и % опоздавших доставок
- Доход и расходы по типу оплаты

## 🧮 DAX-формулы

Вот некоторые ключевые меры, используемые в отчете:

```dax
Revenue = orders[Quantity] * RELATED(products[UnitPrice])

DeliveryDays = DATEDIFF(logistics[ShippedDate], logistics[DeliveredDate], DAY)

Average Delivery Days = AVERAGE(logistics[DeliveryDays])

LateDays = DATEDIFF(logistics[ExpectedDate], logistics[DeliveredDate], DAY)

DeliveredOnTime = IF(logistics[DeliveredDate] <= logistics[ExpectedDate], "On Time", "Late")

On Time Deliveries % = 
VAR TotalDelivered = COUNTROWS(logistics)
VAR OnTime = CALCULATE(COUNTROWS(logistics), logistics[DeliveredDate] <= logistics[ExpectedDate])
RETURN DIVIDE(OnTime, TotalDelivered)

📂 Источник данных
Данные — синтетические, основанные на типичной структуре ecommerce-данных:

Заказы: orders.csv

Клиенты: customers.csv

Продукты: products.csv

Оплаты: payments.csv

Логистика: logistics.csv

🛠 Используемые технологии
Power BI Desktop

DAX (Data Analysis Expressions)

Модель "звезда" с таблицами-фактами и справочниками

💼 Цель проекта
Этот дашборд создан как часть портфолио начинающего дата-аналитика и демонстрирует навыки:

Построения модели данных

Визуализации KPI

Написания DAX-формул

Анализа бизнес-процессов онлайн-торговли
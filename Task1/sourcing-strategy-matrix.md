# sourcing-strategy-matrix

**Целевые модели:**

- **SaaS (Buy)** — готовые решения для стандартизированных процессов.
- **PaaS/IaaS (Migrate / Build in Cloud)** — перенос в облако уникальных внутренних систем (managed DB, iPaaS, event streaming).
- **In-house / on-premises** — то, что технически или по соображениям безопасности нельзя переносить, либо это конкурентное преимущество.

---

## Матрица решений Buy vs Build


|№|L1 (Направление)|L2 (Бизнес-возможность)|Целевая модель|As-Is|Промежуточное (2 мес.)|Финальное (1 год)|Обоснование|
|:---|:---|:---|:---|:---|:---|:---|:---|
|1|Управление сетью и развитие (M&A)|M&A Pipeline|SaaS|Excel, ручной скоринг|Внедрение SaaS CRM/Deal Management|Полностью в SaaS|Стандартная функция. Нет смысла строить.|
|2|Управление сетью и развитие (M&A)|Post-Merger Integration|PaaS|Ручной конвейер|Пилот iPaaS \+ ML-matching|Полная автоматизация на PaaS|Уникальный процесс, но автоматизируемый. iPaaS \+ кастомная логика.|
|3|Управление сетью и развитие (M&A)|Store Launch|SaaS \+ PaaS|2 недели, выезд бригады|Пилот zero-touch в 10 магазинах|Открытие за 5 дней без выезда|Cloud POS — SaaS. Zero-touch provisioning — PaaS.|
|4|Розничные продажи|POS Operations|SaaS|Толстый клиент, монолит|Пилот Cloud POS в 10–20 точках|Полный переход на Cloud POS|Стандартная функция, не даёт конкурентного преимущества. Cloud POS — зрелый рынок.|
|5|Розничные продажи|Payment Processing|SaaS|Прямая интеграция, USB/COM|Payment Gateway \+ HAL, пилот|Все терминалы через Gateway|Стандартная функция \+ compliance (PCI DSS). Строить самим — риск и дорого.|
|6|Розничные продажи|Offline Sales|PaaS|Табличка «Только наличные»|Offline-first: кэш \+ очередь|Полный offline-first с reconciliation|Часть Cloud POS, но требует кастомной логики sync.|
|7|Розничные продажи|Возвраты и обмены|SaaS|В POS|Вместе с Cloud POS|Вместе с Cloud POS|Входит в Cloud POS.|
|8|Управление ассортиментом|SKU Management|PaaS (Buy \+ Build)|VLOOKUP \+ 80% вручную|Пилот ML-matching на 1 сети|80%\+ автоматизации|ML-based matching — buy компоненты (embeddings API), логика — build.|
|9|Управление ассортиментом|Pricing|In-house (SAP)|SAP ERP|SAP в private cloud|SAP в private cloud|Уникальная логика ценообразования в SAP. Не трогать.|
|10|Управление ассортиментом|Promo Management|In-house|Promo Engine (own)|Обернуть в API|Сохранить, интегрировать|Уникальное конкурентное преимущество.|
|11|Маркетинг и лояльность|Loyalty Program|SaaS \+ PaaS|Зависит от SAP online|SaaS \+ offline-кэш|Полностью в SaaS \+ offline|SaaS для программы, PaaS для offline-кэша.|
|12|Маркетинг и лояльность|Omnichannel Marketing|SaaS|Не выражен|Внедрение CDP|Полностью в SaaS|Стандартная функция.|
|13|Логистика и запасы|Inventory Management|In-house (SAP)|SAP ERP|SAP в private cloud|SAP в private cloud|Учёт остатков — ядро SAP.|
|14|Логистика и запасы|Omnichannel Fulfillment|In-house|Smart Fulfillment (own)|Обернуть в API|Сохранить, интегрировать|Уникальное конкурентное преимущество.|
|15|Логистика и запасы|Warehouse Logistics|In-house (SAP)|SAP \+ Smart Fulfillment|Разделить bounded contexts|API-слой|Часть SAP и Smart Fulfillment.|
|16|ИТ-инфраструктура|Store Ops Support|SaaS|Ручной разбор|Внедрение SaaS ITSM \+ monitoring|Proactive support, 70%\+ автоматики|ITSM/мониторинг — зрелый рынок (ServiceNow, Datadog).|
|17|ИТ-инфраструктура|Local Infrastructure|IaaS/PaaS|500\+ локальных серверов|Аудит \+ пилот миграции 20–50 точек|Локальные серверы ликвидированы|Ядро TCO-экономии. Managed DB вместо MS SQL Express.|
|18|ИТ-инфраструктура|SAP Integration|PaaS (iPaaS)|Ночной FTP|API-слой над SAP|Kafka/Event-driven|API-слой \+ event streaming.|
|19|ИТ-инфраструктура|Cloud Infrastructure|IaaS/PaaS|Отсутствует|Выбор провайдера (AWS/GCP/Azure)|Полностью в облаке|Базовая инфраструктура для всего остального.|
|20|ИТ-инфраструктура|Equipment Management (HQ)|SaaS \+ PaaS|Разнородный парк|SaaS ITAM \+ HAL|Единый реестр \+ zero-touch|ITAM/CMDB — SaaS. HAL — build на PaaS.|
|21|Интеграция данных|SKU Matching|PaaS|Ручной, 80%|Пилот ML-matching|80%\+ автоматизации|ML API \+ кастомная логика.|
|22|Интеграция данных|Data Migration|PaaS (iPaaS)|CSV/XLS email|iPaaS \+ staging area|Полная автоматизация|iPaaS (MuleSoft, Boomi) \+ кастомная валидация.|
|23|Интеграция данных|Reference Sync|PaaS (iPaaS)|Ночной FTP|Event-driven для критичных|Real-time / near-real-time|Event-driven sync.|
|24|Финансы и учёт|Бухгалтерский учёт|In-house (SAP)|SAP ERP|SAP private cloud|SAP private cloud|Ядро учёта.|
|25|Финансы и учёт|Кадровый учёт|In-house (SAP)|SAP ERP|SAP private cloud|SAP private cloud|Ядро учёта.|
|26|Финансы и учёт|Финансовое планирование|In-house (SAP)|SAP ERP|SAP private cloud|SAP private cloud|Ядро учёта.|
|27|Управление персоналом|Найм и адаптация|SaaS|Стандартно|Внедрение HRM SaaS|Полностью в SaaS|Стандартная функция (HRM SaaS).|
|28|Управление персоналом|Обучение персонала|SaaS|Стандартно|Внедрение LMS|Полностью в SaaS|Стандартная функция (LMS SaaS).|
|29|Управление персоналом|Управление ФОТ|In-house (SAP)|SAP ERP|SAP private cloud|SAP private cloud|В SAP.|
|30|Управление магазинами|Стандартизация процессов|PaaS \+ SaaS|Хаос после M&A|Единые регламенты \+ шаблоны|Полная стандартизация|Регламенты — build на PaaS. Обучение — SaaS.|
|31|Управление магазинами|Контроль качества обслуживания|SaaS|Стандартно|Внедрение SaaS|Полностью в SaaS|Стандартная функция (CX-платформа).|
|32|Управление магазинами|Equipment Management (Store)|SaaS \+ PaaS|Разрозненно|SaaS ITAM \+ HAL|Централизованное управление|Единый реестр. Дублирование с №20.|

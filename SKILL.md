---
name: it-company
description: Запускает конвейер из 37 специализированных суб-агентов (продуктовый дискавери, бизнес-анализ, продукт-менеджмент, архитектура, security-архитектура, БД, backend по цепочке логика→API→интеграция, ML/CV по той же цепочке, frontend по цепочке логика→UI-компоненты→интеграция, UX/UI, тест-архитектура, автотесты по тест-пирамиде unit→integration→E2E, ручной QA, инфраструктура-архитектура, DevOps по цепочке build→CI/CD→release, SRE, security-аудит по цепочке логика→API→инфраструктура/консолидация, техписатель, код-ревью, пентест) — каждый агент работает только в своей узкой области и передаёт результат следующему, как в настоящей продуктовой IT-компании. Используй, когда пользователь хочет построить продукт или крупную фичу с нуля через полноценный, профессиональный процесс разработки, а не быстрый набросок кода. Триггеры: "построй продукт", "с нуля", "как настоящая компания", "полный цикл разработки", "/it-company".
---

# Virtual IT Company

Ты — оркестратор виртуальной IT-компании. Вместо того чтобы делать всё
самому одним потоком мыслей, ты проводишь запрос пользователя через
конвейер из 37 ролей. Каждая роль — это **отдельный суб-агент** с узкой
зоной ответственности, который получает только нужный ему контекст,
выполняет свою работу профессионально и передаёт результат дальше.
Это сознательное архитектурное решение пользователя: специализация даёт
лучший результат, чем одна модель, пытающаяся удержать в голове всё сразу.
Четыре роли (13–15 и 31) — условные, см. секцию «Условные роли» ниже.

Шесть блоков конвейера построены по единому паттерну **внутреннее →
внешнее → интеграция**:
- **backend** (9–12): бизнес-логика → HTTP API → сборка и проверка целиком;
- **ML/CV** (13–15, условно): ядро модели → сервисный слой инференса →
  подключение к backend;
- **frontend** (16–21): состояние/данные → визуальные компоненты →
  сборка приложения целиком;
- **автотесты** (22–25): стратегия → unit → integration → E2E
  (классическая тест-пирамида);
- **DevOps** (27–30): архитектура инфраструктуры → сборка/контейнеризация
  → CI/CD-пайплайн → реальный деплой;
- **security-аудит** (32–34): бизнес-логика → API-слой →
  инфраструктура/CI-CD + консолидация всех находок в один отчёт.

Каждый шаг внутри блока — чистая граница ответственности с чётким
файловым/документным артефактом на входе и выходе, а не параллельная
работа над одним и тем же кодом. Показательно, что в четырёх из шести
блоков (backend, ML/CV, frontend, security) внутреннее/внешнее деление
буквально совпадает: security-аудиторы проверяют ровно те же слои
(Business Logic / API / Infra), которые строили соответствующие
разработчики — это не совпадение, а прямое следствие того, что аудит
организован по тем же архитектурным границам, что и сама система.

## Конвейер ролей

| # | Роль | Файл брифа | Ключевой результат |
|---|------|-----------|---------------------|
| 1 | Product Discovery Manager | [roles/01-product-discovery-manager.md](roles/01-product-discovery-manager.md) | Product Vision, PRD, roadmap |
| 2 | Business Analyst | [roles/02-business-analyst.md](roles/02-business-analyst.md) | User Stories, Use Cases, Business Requirements |
| 3 | Product Manager | [roles/03-product-manager.md](roles/03-product-manager.md) | Backlog, Epics/Features, приоритеты |
| 4 | Solution Architect | [roles/04-solution-architect.md](roles/04-solution-architect.md) | Architecture Document |
| 5 | Security Architect | [roles/05-security-architect.md](roles/05-security-architect.md) | Threat Model, Security Requirements |
| 6 | System Analyst | [roles/06-system-analyst.md](roles/06-system-analyst.md) | Sequence/Activity/State/Flow диаграммы |
| 7 | Database Architect | [roles/07-database-architect.md](roles/07-database-architect.md) | ER-диаграмма, логическая схема БД |
| 8 | Database Engineer | [roles/08-database-engineer.md](roles/08-database-engineer.md) | Миграции, индекс-стратегия, бэкапы |
| 9 | Backend Architect | [roles/09-backend-architect.md](roles/09-backend-architect.md) | Backend-архитектура, контракты Logic/API |
| 10 | Backend Business Logic Developer | [roles/10-backend-logic-developer.md](roles/10-backend-logic-developer.md) | Service/Domain Layer + unit-тесты |
| 11 | Backend API Layer Developer | [roles/11-backend-api-developer.md](roles/11-backend-api-developer.md) | HTTP-слой поверх готовой логики |
| 12 | Backend Integration Engineer | [roles/12-backend-integration-engineer.md](roles/12-backend-integration-engineer.md) | Собранный и проверенный backend |
| 13 | ML/CV Logic Developer *(условно)* | [roles/13-ml-cv-logic-developer.md](roles/13-ml-cv-logic-developer.md) | Ядро модели/пайплайна, метрики |
| 14 | ML/CV Serving Engineer *(условно)* | [roles/14-ml-cv-serving-engineer.md](roles/14-ml-cv-serving-engineer.md) | Сервисный слой инференса |
| 15 | ML/CV Integration Engineer *(условно)* | [roles/15-ml-cv-integration-engineer.md](roles/15-ml-cv-integration-engineer.md) | ML-сервис, подключённый к backend |
| 16 | Frontend Architect | [roles/16-frontend-architect.md](roles/16-frontend-architect.md) | Frontend-архитектура, контракты Logic/UI |
| 17 | UX Designer | [roles/17-ux-designer.md](roles/17-ux-designer.md) | User Flow, Wireframes |
| 18 | UI Designer | [roles/18-ui-designer.md](roles/18-ui-designer.md) | UI Kit, дизайн-система |
| 19 | Frontend Logic Developer | [roles/19-frontend-logic-developer.md](roles/19-frontend-logic-developer.md) | Состояние/hooks/data-fetching |
| 20 | UI Component Developer | [roles/20-ui-component-developer.md](roles/20-ui-component-developer.md) | Страницы и визуальные компоненты |
| 21 | Frontend Integration Engineer | [roles/21-frontend-integration-engineer.md](roles/21-frontend-integration-engineer.md) | Собранное и проверенное приложение |
| 22 | QA Lead / Test Architect | [roles/22-qa-lead.md](roles/22-qa-lead.md) | Test Strategy, Test Plan |
| 23 | Unit Test Engineer | [roles/23-unit-test-engineer.md](roles/23-unit-test-engineer.md) | Unit-тесты бизнес-логики |
| 24 | Integration Test Engineer | [roles/24-integration-test-engineer.md](roles/24-integration-test-engineer.md) | Integration-тесты на стыках компонентов |
| 25 | E2E Test Automation Engineer | [roles/25-e2e-test-automation-engineer.md](roles/25-e2e-test-automation-engineer.md) | E2E-тесты, единый автотестовый прогон |
| 26 | Manual QA Engineer | [roles/26-manual-qa-engineer.md](roles/26-manual-qa-engineer.md) | Найденные баги, вердикт готовности |
| 27 | Infrastructure Architect | [roles/27-infrastructure-architect.md](roles/27-infrastructure-architect.md) | Инфраструктурная стратегия |
| 28 | DevOps Build Engineer | [roles/28-devops-build-engineer.md](roles/28-devops-build-engineer.md) | Dockerfile/compose, рабочая сборка |
| 29 | CI/CD Pipeline Engineer | [roles/29-cicd-pipeline-engineer.md](roles/29-cicd-pipeline-engineer.md) | Пайплайн сборки/тестов/деплоя |
| 30 | Release Integration Engineer | [roles/30-release-integration-engineer.md](roles/30-release-integration-engineer.md) | Реальный деплой, сервер/SSL/секреты |
| 31 | SRE *(условно)* | [roles/31-sre.md](roles/31-sre.md) | Мониторинг, алертинг, SLO, runbook |
| 32 | Application Security Engineer | [roles/32-application-security-engineer.md](roles/32-application-security-engineer.md) | Аудит безопасности бизнес-логики |
| 33 | API Security Engineer | [roles/33-api-security-engineer.md](roles/33-api-security-engineer.md) | Аудит безопасности API-слоя |
| 34 | Security Integration Auditor | [roles/34-security-integration-auditor.md](roles/34-security-integration-auditor.md) | Аудит инфраструктуры + сводный отчёт |
| 35 | Technical Writer | [roles/35-technical-writer.md](roles/35-technical-writer.md) | README, документация |
| 36 | Code Reviewer | [roles/36-code-reviewer.md](roles/36-code-reviewer.md) | Финальное одобрение / список правок |
| 37 | Penetration Tester | [roles/37-penetration-tester.md](roles/37-penetration-tester.md) | Отчёт по динамическому редтим-аудиту |

## Условные роли

Роли 13–15 (ML/CV Logic/Serving/Integration) и 31 (SRE) включаются в
конвейер не всегда:
- **ML/CV-блок (13–15)** — только если продукт содержит ML/CV/AI-компонент
  (распознавание, детекция, классификация, генерация и т.п.). Для обычных
  CRUD-продуктов без модельной части — пропускается целиком, всеми тремя
  ролями сразу.
- **SRE (31)** — только для проектов с реальной production-нагрузкой и/или
  явными SLA-требованиями. Для небольших внутренних инструментов и MVP —
  пропускается.

Реши на этапе 1 (Product Discovery), нужны ли эти роли для конкретного
продукта, и заведи задачи в TaskCreate только на реально нужные этапы —
не создавай задачу на пропущенную условную роль.

## Как вести оркестрацию

### 0. Подготовка
Заведи в проекте (или, если проекта ещё нет — спроси пользователя куда)
папку `docs/it-company/`. Каждый этап сохраняет туда свой результат как
`NN-role-name.md`. Это единственный способ передавать контекст между
суб-агентами — не полагайся на память между вызовами.

Заведи задачи через `TaskCreate` на все нужные этапы (31, 34 или 37, в
зависимости от того, какие условные роли включены — см. выше), отмечай
выполненными по ходу — это даёт пользователю видимость прогресса.

### 1. Этап 1 — веди сам, не суб-агентом
Product Discovery Manager (роль 1) требует живого, открытого диалога с
пользователем — сколько угодно вопросов, пока не станет понятно на 100%.
Суб-агенты не умеют вести такой диалог естественно, поэтому **этот этап
ты проводишь напрямую**, следуя брифу в `roles/01-product-discovery-manager.md`.
На этом же этапе реши, нужны ли условные роли 13–15 и 31 (см. «Условные
роли»). Не переходи к этапу 2, пока не закрыл все пункты брифа и не
сохранил итоговые документы в `docs/it-company/01-product-discovery-manager.md`.

### 2. Этапы 2–37 — суб-агенты
Для каждого следующего этапа (кроме пропущенных условных) вызывай `Agent`
с `subagent_type: "general-purpose"` (это фреш-агент без памяти о
разговоре — так и задумано, у него должен быть только тот контекст,
который нужен для его роли, как у нового сотрудника). В промпте:
- вставь **целиком** содержимое соответствующего `roles/NN-*.md`;
- вставь только те документы предыдущих этапов, которые реально нужны
  этой роли (см. секцию «Получает от предыдущих этапов» в брифе роли) —
  не весь `docs/it-company/`, а именно относящееся к делу;
- явно попроси вернуть финальный результат в готовом для сохранения
  виде (markdown/код), а не пересказ того, что агент собирается сделать.

После каждого этапа: сохрани результат в `docs/it-company/NN-role-name.md`
(или в соответствующие файлы кода проекта, если этап — разработка),
отметь задачу выполненной, дай пользователю одно-два предложения о том,
что сделано, и переходи дальше.

Внутри каждого из шести последовательных блоков (backend: 10–12, ML/CV:
13–15, frontend: 19–21, автотесты: 23–25, DevOps: 28–30, security-аудит:
32–34) следующий агент **всегда** получает отчёт предыдущего как готовый,
рабочий результат, а не как черновик для переделки — если он находит
пробел на стыке, он фиксирует это явно (см. «Не делай» в брифе
соответствующей роли), а не переписывает чужой слой с нуля.

### 3. Контрольные точки с пользователем
Этапы 10 (Backend Business Logic Developer), 19 (Frontend Logic
Developer) и 28 (DevOps Build Engineer) — первые точки в своих блоках,
где пишется реальный код и много файлов; это дорого и не всегда
обратимо одним движением. Перед стартом каждого из исполнительских
блоков (backend: 10–12, frontend: 19–21, DevOps: 28–30, и ML/CV: 13–15
если включён) коротко подтверди с пользователем объём и технологии (если
ещё не зафиксированы в Architecture Document/Infrastructure Strategy),
прежде чем агенты начнут массово создавать файлы.

### 4. Code Reviewer и цикл возврата
Этап 36 (Code Reviewer) получает **все** документы и весь код. Если он
находит несоответствия, он должен явно указать, какому этапу/роли
вернуть задачу и что именно исправить. Ты (оркестратор):
1. вызываешь Agent нужного этапа заново с его прежним брифом + конкретным
   списком замечаний от ревьюера;
2. после исправления повторно вызываешь Code Reviewer на обновлённые
   материалы.
Ограничь цикл 3 итерациями — если после трёх кругов ревьюер всё ещё не
одобряет, останови конвейер и опиши пользователю, что застряло и почему,
вместо того чтобы крутить цикл бесконечно.

### 4a. Penetration Tester и цикл возврата
После одобрения Code Reviewer запускается этап 37 (Penetration Tester) —
активный аудит запущенного инстанса (см. `roles/37-penetration-tester.md`,
включая предпосылку авторизации и границы «Не делай»). Перед его стартом
уточни у пользователя адрес поднятого для тестирования инстанса, если он
ещё не зафиксирован. Если найдены critical/high находки — тот же цикл
возврата, что и с Code Reviewer: соответствующий разработчик исправляет,
затем повторно вызываются Security Integration Auditor (34) и
Penetration Tester (37). Тот же лимит — 3 итерации.

Все три security-аудитора (32–34) и Penetration Tester (37) подтягивают
конкретные плейбуки из внешней библиотеки
[mukul975/Anthropic-Cybersecurity-Skills](https://github.com/mukul975/Anthropic-Cybersecurity-Skills)
через `WebFetch` — список релевантных пунктов см. в самих файлах брифов,
поделённый по слоям (логика / API / инфраструктура / динамический аудит).
Это community-библиотека (не от Anthropic), но подробнее и точнее
generic-чек-листов; вендорить её содержимое в этот репозиторий не нужно.

### 5. Границы ролей
Каждый суб-агент работает **только** в своей области (см. «Не делай» в
его брифе). Не позволяй, например, API Layer Developer-у переписывать
бизнес-логику, Unit Test Engineer-у писать E2E-сценарии или API Security
Engineer-у лезть в аудит инфраструктуры — если агент считает, что
проблема лежит в чужой зоне ответственности, он должен сообщить об этом
в своём отчёте, а не чинить сам. Это особенно важно на стыках:
- архитектор ↔ инженер: Database Architect↔Database Engineer,
  Infrastructure Architect↔DevOps-блок, Security Architect↔security-аудит
  — первый решает «что и почему», второй реализует/проверяет «как»;
- внутреннее ↔ внешнее ↔ интеграция: внутри каждого из шести
  последовательных блоков (9–12, 13–15, 16–21, 22–26, 27–30, 32–34)
  каждый следующий агент потребляет готовый результат предыдущего через
  его публичный интерфейс/отчёт, а не переписывает его.

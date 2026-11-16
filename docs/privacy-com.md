# Privacy.com: опись продукта для «Шлюза»

Снято 16.11.2026 с открытых страниц www.privacy.com (по `sitemap.xml`) и developers.privacy.com. Справка support.privacy.com отдаёт 403, её не открывали: факты оттуда взяты из поисковой выдачи и помечены **«по выдаче»**. Сырые копии страниц лежат в scratchpad сессии (`privacy-raw/`), в репозиторий не кладём.

Сокращения ссылок: `P` = https://www.privacy.com, `D` = https://developers.privacy.com, `S` = https://support.privacy.com/hc/en-us/articles.

**Что не открылось или чего нет:**
- `support.privacy.com`: 403 для этой среды, блокировку не обходили, данные только по выдаче.
- `P/how-it-works`, `P/features`, `P/commercial`, `P/faq` отдают 404, таких страниц нет. Вместо них в меню сайта стоят: «How Privacy Cards Work» → [P/unique-card-number](https://www.privacy.com/unique-card-number), функции → [P/virtual-cards](https://www.privacy.com/virtual-cards) и [P/control](https://www.privacy.com/control), бизнес → [P/business](https://www.privacy.com/business).
- `agents.privacy.com` (страница MCP и CLI) не открывали, взяли [блог про MCP](https://www.privacy.com/blog/privacy-mcp-connect-ai-assistant-privacy-account) и [D/docs/mcp-server](https://developers.privacy.com/docs/mcp-server).
- `P/cardholder-agreement-byline` по тексту совпадает с [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) побайтно, в обоих эмитент Patriot Bank. Отдельная версия под Byline Bank есть только для бизнеса: [P/commercial-cardholder-agreement-byline](https://www.privacy.com/commercial-cardholder-agreement-byline).
- `P/card-terms` состоит из старых General Terms от «Pay With Privacy, Inc.» и коммерческого договора Patriot Bank, выглядит как устаревшая копия.
- Блог прочитан только там, где он про механику продукта (18 постов, список в конце). Около 400 SEO-статей («как отменить Netflix», обзоры VPN) пропущены.

---

## 1. Как устроено юридически

| Что | Факт | Источник |
|---|---|---|
| Компания | Lithic, Inc. (бывшая Pay with Privacy, Inc.), d/b/a Privacy.com, Нью-Йорк, 228 Park Ave S, PMB 57488. Основана в 2014 году | [P/terms](https://www.privacy.com/terms), [P/about](https://www.privacy.com/about) |
| Роль Privacy | **Программный менеджер**, то есть агент и подрядчик банка. «Мы не банк», банковские услуги оказывает банк-партнёр | [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §1, [P/terms](https://www.privacy.com/terms) §1 |
| Эмитенты | Patriot Bank, N.A. и Byline Bank, оба члены FDIC, по лицензиям Mastercard и Visa | подвал всех страниц, напр. [P/pricing](https://www.privacy.com/pricing) |
| Потребительские карты | Visa и/или Mastercard, эмитент Patriot Bank (договор от 06.05.2024) | [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) |
| Бизнес-карты | Mastercard от Byline Bank (новая версия) или Visa/MC от Patriot Bank (старая) | [P/commercial-cardholder-agreement-byline](https://www.privacy.com/commercial-cardholder-agreement-byline), [P/commercial-cardholder-agreement](https://www.privacy.com/commercial-cardholder-agreement) |
| **Тип карты** | **Charge card**, то есть кредитная линия банка с погашением в конце цикла. Прямо сказано: «не дебетовая и не предоплаченная». Обеспечена **Secured Account**: резервный счёт в банке на имя клиента, средства в пуле, проценты не начисляются | [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §1, §7 |
| Лимит | Credit Limit «в основном по сумме на вашем внешнем счёте». Available Credit = лимит минус непогашенное за цикл | там же §2–3 |
| Цикл | **14 дней**, оплата через 14 дней после конца цикла. По ходу цикла идут Daily Payments (автодебет с внешнего счёта), поэтому в выписке обычно $0 | там же §2, §4 |
| Источник денег | Расчётный счёт в банке США через Plaid (логин хранит Plaid, Privacy получает токен) или дебетовая карта. С карты Visa debit списания идут «пакетом», одним за 24 часа | [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §5e, [блог о безопасности](https://www.privacy.com/blog/is-privacy-com-safe-an-overview-of-privacys-security-practices), [P/card-funding-authorization](https://www.privacy.com/card-funding-authorization); пакеты — [S/25651041228439](https://support.privacy.com/hc/en-us/articles/25651041228439-What-are-Grouped-Payments) (по выдаче) |
| Процессинг | Свой issuer processor, на нём же построен B2B-продукт Lithic | [P/about](https://www.privacy.com/about), [блог: Privacy → Lithic](https://www.privacy.com/blog/our-journey-from-privacy-com-to-lithic) |
| Как зарабатывают | Интерчейндж с продавцов плюс подписки. «Данные не продаём» | [P/](https://www.privacy.com), [P/private-and-discreet-payments](https://www.privacy.com/private-and-discreet-payments) |
| Кредитная история | Кредитный запрос не делается, в отчёте карты не видны. При этом в договоре есть право сообщать данные в бюро | [P/](https://www.privacy.com) FAQ; договор §13 l |
| Кто может | Граждане и резиденты США, 18+, со счётом в банке или кредитном союзе США | [P/](https://www.privacy.com) FAQ, [P/terms](https://www.privacy.com/terms) §13 |
| Масштаб | «600k+ пользователей» (на старых страницах «250K+»), «более $3B оборота» | [P/](https://www.privacy.com), [P/control](https://www.privacy.com/control) |

**Вывод для нас:** Privacy — не кошелёк с остатком, а кредитная карта, которая каждый день погашается списанием с банковского счёта клиента. Модель «Шлюза» (пополняемый кошелёк плюс карты) ближе к предоплаченной. Privacy специально подчёркивает, что он не prepaid.

---

## 2. Путь клиента от регистрации до первой покупки

1. **«Sign Up»** на сайте или в приложении: «примерно 3 минуты». [P/virtual-card](https://www.privacy.com/virtual-card), [P/business](https://www.privacy.com/business)
2. **Данные для KYC:** имя, дата рождения, телефон, email, адрес, государственный идентификационный номер (SSN). [P/virtual-card](https://www.privacy.com/virtual-card), [P/unique-card-number](https://www.privacy.com/unique-card-number), [P/privacy-policy](https://www.privacy.com/privacy-policy)
3. **Проверка личности** сторонними сервисами. В «небольшом проценте случаев» просят **селфи и фото документа** через Persona. Основание — Bank Secrecy Act и USA PATRIOT Act. Ремарка: «Privacy не анонимный счёт». [P/our-commitment](https://www.privacy.com/our-commitment)
4. **Согласия:** Terms, E-Sign Consent (без согласия на электронные документы счёт не открыть), ACH Authorization (списания до **$10 000 за рабочий день**, несколько раз в день, без уведомлений), Card Funding Authorization (если источник — карта), договор держателя. [P/e-sign-consent](https://www.privacy.com/e-sign-consent), [P/ach](https://www.privacy.com/ach), [P/card-funding-authorization](https://www.privacy.com/card-funding-authorization)
5. **Источник денег.** Банк через Plaid: логин вводится в окне Plaid, Privacy получает номер счёта и routing. Или дебетовая карта: «Account → Add Funding Source → Link Debit Card», номер и адрес плательщика. Ошибки при подключении: «Please try connecting a different account», «No available accounts», «Account not currently supported», «Could not link bank account». Состояние источника в API: `PENDING` (проверка, например микродепозитами) или `ENABLED`. [S/360040584834](https://support.privacy.com/hc/en-us/articles/360040584834-How-do-I-connect-a-bank-account), [S/360041073133](https://support.privacy.com/hc/en-us/articles/360041073133-How-do-I-connect-a-debit-card), [S/360048575234](https://support.privacy.com/hc/en-us/articles/360048575234-I-tried-adding-my-bank-account-as-a-funding-source-but-it-didn-t-work) (по выдаче); [D/docs/funding-sources](https://developers.privacy.com/docs/funding-sources)
6. **Ожидание проверки:** «как только аккаунт проверен — можно пользоваться картами». [P/unique-card-number](https://www.privacy.com/unique-card-number)
7. **Создание карты** в веб-приложении, мобильном приложении или расширении («в два клика»). Выбираются тип (Single-Use, Merchant-Locked, Category-Locked, Everywhere), лимит и период лимита, имя или заметка, цвет и эмодзи. [P/unique-card-number](https://www.privacy.com/unique-card-number), [блог: новое приложение](https://www.privacy.com/blog/introducing-redesigned-privacy-mobile-app-for-ios-android)
8. **Оплата:** расширение само подставляет номер, CVV и срок в форму оплаты, либо их копируют вручную. Merchant-Locked карта **привязывается к первому магазину**, где прошла оплата. [P/browser-extension](https://www.privacy.com/browser-extension), [D/docs/cards](https://developers.privacy.com/docs/cards)
9. **Уведомление** о покупке приходит пушем и/или письмом. Деньги списываются с источника (для банка — ежедневным Daily Payment). [P/unique-card-number](https://www.privacy.com/unique-card-number), [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement)

Экраны приложения после редизайна: нижнее меню **Wallet · Activity · Account**. [блог: новое приложение](https://www.privacy.com/blog/introducing-redesigned-privacy-mobile-app-for-ios-android)

---

## 3. Функции карт и аккаунта

| Функция | Что делает | Тариф | Детали и источник |
|---|---|---|---|
| **Merchant-Locked Card** | Привязывается к первому магазину, в других местах отказ | все | API `MERCHANT_LOCKED`, `hostname` = магазин. [P/merchant-cards](https://www.privacy.com/merchant-cards), [D/docs/cards](https://developers.privacy.com/docs/cards) |
| **Single-Use Card** | Закрывается «вскоре после первой операции». Повторная попытка списания отклоняется, клиенту приходит уведомление | все | Отказ `SINGLE_USE_RECHARGED`. [P/single-use-cards](https://www.privacy.com/single-use-cards), [D/docs/transactions](https://developers.privacy.com/docs/transactions) |
| **Category-Locked Card** | Работает только в одной категории продавцов: Dining, Groceries, Food Delivery, Online Retail, Streaming, Subscriptions & Utilities. Вне категории отказ | Plus+ | Лимиты: на операцию, неделю, месяц, всё время. [P/category-cards](https://www.privacy.com/category-cards), [блог Plus](https://www.privacy.com/blog/introducing-privacy-plus-plan) |
| **Everywhere Card** | Не привязывается к магазину. Добавляется в Apple, Google или Samsung Wallet для оплаты касанием, работает и онлайн | Pro, Premium | Не больше **3 открытых**. Кэшбэк по ним не начисляется. Добавление прямо из приложения (push provisioning). Только для Pro и Premium, потому что у кошельков свои комиссии и другой фрод. API `DIGITAL_WALLET`. [P/everywhere-cards](https://www.privacy.com/everywhere-cards), [блог Everywhere](https://www.privacy.com/blog/introducing-privacy-everywhere-cards) |
| **Лимит на карту** | Сумма и период: на операцию, месяц, год, за всё время (Category — ещё неделя). Превышение отклоняется, клиенту уведомление | все | Целые доллары. Окна скользящие (подробно в разд. 4). [P/spend-limits](https://www.privacy.com/spend-limits), [D/docs/cards](https://developers.privacy.com/docs/cards) |
| **Пауза** | Временно отклоняет все списания, снимается в любой момент | все | Сценарии: утечка у продавца, подозрение, потеря телефона, общая карта не в работе, отмена подписки. [P/pause-close](https://www.privacy.com/pause-close) |
| **Закрытие** | Навсегда, без возврата. Закрытые карты из списка не удаляются | все | [P/pause-close](https://www.privacy.com/pause-close); [S/360041865433](https://support.privacy.com/hc/en-us/articles/360041865433-Can-closed-Privacy-Cards-be-removed-deleted-from-my-account) (по выдаче) |
| **Автопауза неиспользуемых** | Карта без операций **больше года** встаёт на паузу сама | все | [S/20321316268439](https://support.privacy.com/hc/en-us/articles/20321316268439-Why-was-my-Privacy-Card-paused-without-my-knowledge) (по выдаче) |
| **Card Notes** | Заметка к карте (о продавце, когда ждать списание) | Plus+ | [блог Plus](https://www.privacy.com/blog/introducing-privacy-plus-plan) |
| **Card Sharing** | Поделиться картой с близким или сотрудником «в один клик». Владелец сохраняет лимиты, паузу и закрытие. Через API: письмо с защищённой ссылкой на номер, CVV и срок, ссылка истекает | Plus+ | [P/pricing](https://www.privacy.com/pricing), [P/](https://www.privacy.com) FAQ, [D/reference/share](https://developers.privacy.com/reference/post_cards-card-token-share) |
| **Оформление карты** | Цвет (палитра) и эмодзи | все | [P/mobile-app](https://www.privacy.com/mobile-app), [блог: приложение](https://www.privacy.com/blog/introducing-redesigned-privacy-mobile-app-for-ios-android) |
| **Избранное и быстрые жесты** | Свайп вправо: в избранное, пауза или снятие паузы. Избранные закреплены сверху | все | там же |
| **Сортировка, фильтры, поиск** | Сортировка и фильтры кошелька, поиск по операциям | все | там же |
| **Спор из приложения** | Открыть спор по операции с телефона | все | там же |
| **Private Spend Mode** | Банк клиента видит в выписке только «Privacy.com», без названия магазина. Действует для будущих операций, в Privacy история полная | (тариф не указан) | [P/private-and-discreet-payments](https://www.privacy.com/private-and-discreet-payments); в 2019 году было в Pro как «Discreet merchants» ([блог 2019](https://www.privacy.com/blog/subscription-plan)) |
| **Уведомления** | О каждой операции (пуш, email), об отказах, синхронизация между устройствами | все | [P/business](https://www.privacy.com/business), [P/mobile-app](https://www.privacy.com/mobile-app) |
| **Кэшбэк 1%** | На eligible-покупки до **$4 500 в месяц**. Начисляется Privacy Credits в первые 10 рабочих дней следующего месяца. Сгорает после 12 месяцев неактивности, не выводится и не передаётся. Everywhere-карты не участвуют | Pro, Premium | [P/pricing](https://www.privacy.com/pricing), [P/terms](https://www.privacy.com/terms) §2 |
| **Без комиссии за границей** | 0% вместо 3% | Pro, Premium | [P/pricing](https://www.privacy.com/pricing) |
| **Поддержка в чате** | Live chat в приложении, пн–пт 9:00–17:00 ET | Plus+ | [блог Plus](https://www.privacy.com/blog/introducing-privacy-plus-plan) |
| **API** | Создание и настройка карт, операции, вебхуки, песочница | Plus+ | [D/docs/api-basics](https://developers.privacy.com/docs/api-basics) |
| **MCP и CLI** | Подключение Claude или ChatGPT по OAuth (`https://mcp.privacy.com`): «поставь на паузу все карты», «создай одноразовую на $50», «какие карты не использовались — закрой», «сколько ушло на доставку». Плюс локальный MCP по API-ключу и CLI | Plus+ (нужен API) | [блог MCP](https://www.privacy.com/blog/privacy-mcp-connect-ai-assistant-privacy-account), [P/ai](https://www.privacy.com/ai) |
| **Карты для ИИ-агентов** | Позиционирование: «карта для агента» с привязкой к магазину, лимитом и мгновенной паузой | — | [P/ai](https://www.privacy.com/ai), [блог OpenClaw](https://www.privacy.com/blog/openclaw-ai-agent-spending-virtual-card) |
| **Несколько источников** | Источник по умолчанию и выбор источника на карту (`funding_token`) | все | [D/docs/cards](https://developers.privacy.com/docs/cards); [S/24450641740311](https://support.privacy.com/hc/en-us/articles/24450641740311-What-does-default-funding-source-mean) (по выдаче) |
| **Выписки** | Statement за каждый 14-дневный цикл, скачиваются. История доступна минимум год | все | [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §2h, [P/terms](https://www.privacy.com/terms) §3 |
| **Реферальная программа** | До $5 пригласившему (после регистрации друга и его первой покупки) и до $5 другу на первую покупку | все | [P/terms](https://www.privacy.com/terms) §2 |
| **Партнёрская программа** | Анкета для блогеров | — | [P/affiliate-program](https://www.privacy.com/affiliate-program) |
| **Стейблкоины** | Карты с пополнением стейблкоинами: был лист ожидания, сейчас «закрыт» | — | [P/stablecoins](https://www.privacy.com/stablecoins) |
| **Бизнес** | Карта на поставщика, сотрудника, подписку. Без кредитной проверки, со своим банковским счётом. Сравнение с Ramp: подходит ИП и фрилансерам, есть «делегирование карт сотрудникам». Больше 60 карт — через support | Premium «для малого бизнеса» | [P/business](https://www.privacy.com/business), [P/pricing](https://www.privacy.com/pricing) |
| **2FA** | TOTP (Google Authenticator, 1Password) | все | [блог о безопасности](https://www.privacy.com/blog/is-privacy-com-safe-an-overview-of-privacys-security-practices) |

---

## 4. Лимиты и правила (все числа)

| Правило | Число | Источник |
|---|---|---|
| Новых карт в месяц | Personal 12 · Plus 24 · Pro 36 · Premium 60 | [P/pricing](https://www.privacy.com/pricing) |
| Открытых Everywhere-карт | не больше 3 | [P/pricing](https://www.privacy.com/pricing) |
| Периоды лимита на карту | `TRANSACTION` (каждая операция не выше суммы, операций сколько угодно), `MONTHLY` (скользящий месяц: «та же дата месяц назад»), `ANNUALLY` (календарный год), `FOREVER` (на всю жизнь карты). Category-карты: ещё «weekly» | [D/docs/cards](https://developers.privacy.com/docs/cards), [блог Plus](https://www.privacy.com/blog/introducing-privacy-plus-plan) |
| Лимит в деньгах | целые доллары (в центах, ≥ 0) | [D/docs/cards](https://developers.privacy.com/docs/cards) |
| Лимит аккаунта | Устанавливается по каждому клиенту, меняется алгоритмом или вручную. На экране аккаунта видно, сколько потрачено за 24 часа и 30 дней. Окна скользящие: сутки 24 ч, месяц 30 дней (+6 дней буфер), год 365 дней (+36 ч). В середине месяца не сбрасывается. Как поднять: 1–2 месяца ровных трат, регулярные подписки, упирание в лимиты. **Платный тариф лимит не повышает.** Конкретных сумм в выдаче нет | [S/360011566794](https://support.privacy.com/hc/en-us/articles/360011566794-How-do-spending-limits-work), [S/360012405933](https://support.privacy.com/hc/en-us/articles/360012405933-How-much-can-I-spend-using-Privacy), [S/360042256513](https://support.privacy.com/hc/en-us/articles/360042256513-How-can-I-get-a-higher-spending-limit-on-my-account-) (по выдаче); [P/terms](https://www.privacy.com/terms) §4 «Limits» |
| Отказ из-за остатка в банке | Если операции в обработке приближаются к остатку на счёте клиента | [S/360041447214](https://support.privacy.com/hc/en-us/articles/360041447214) (по выдаче) |
| ACH-списания | до $10 000 за рабочий день, несколько раз в день. Отзыв согласия — за 14 рабочих дней, иначе приостановка или закрытие счёта | [P/ach](https://www.privacy.com/ach) |
| AutoPay | Daily Payment от $0 до $10 000 без предупреждения. Отзыв — за 3 рабочих дня | [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §5a |
| Цикл и срок оплаты | 14 дней, плюс 14 дней на оплату | там же §2 |
| Пакетное списание с Visa debit | Операции за 24 ч одним списанием через 1–5 дней после авторизации. В выписке банка «PWP*Privacy + дата», чек приходит письмом. Подписка на тариф списывается отдельно | [S/25651041228439](https://support.privacy.com/hc/en-us/articles/25651041228439-What-are-Grouped-Payments) (по выдаче) |
| Кэшбэк | 1% до $4 500 в месяц, начисление до 10-го рабочего дня, сгорает через 12 месяцев неактивности. Спор о начислении — в течение 90 дней. Закрыл счёт — за этот месяц кэшбэка нет. За чарджбэки и возвраты ACH могут лишить кэшбэка | [P/terms](https://www.privacy.com/terms) §2 |
| Автопауза | карта без операций > 1 года | [S/20321316268439](https://support.privacy.com/hc/en-us/articles/20321316268439-Why-was-my-Privacy-Card-paused-without-my-knowledge) (по выдаче) |
| Срок карты | Задаётся или генерируется. Истекла — создать новую и сменить у продавца (автоперевыпуска нет) | [D/docs/cards](https://developers.privacy.com/docs/cards); [S/7970204090647](https://support.privacy.com/hc/en-us/articles/7970204090647-What-happens-when-a-Privacy-Card-expires) (по выдаче) |
| Запрещённые отрасли | Атрибутика для незаконного, MLM, рибейт-бизнес, **ставки и лотереи**, выдача наличных, **предоплаченные карты и чеки**, денежные переводы, money orders, валюта, телемаркетинг, «high-risk». Банк вправе отклонять любые азартные операции | [P/terms](https://www.privacy.com/terms) §4, [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §13 j |
| Запрещённые приёмы | Автоматические покупки (боты), абуз «новых пользователей», рефералок и промо продавцов, нарушение правил продавца, перепродажа сервиса, приём денег за третьих лиц | [P/terms](https://www.privacy.com/terms) §4 |
| Авторизованные пользователи | от 13 лет, держатель отвечает за все их операции | [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §1 |
| API | Лимиты по запросам в секунду и в день, блокировка IP за перебор ключей. Страница до 1 000 записей, по умолчанию 50 | [D/docs/api-basics](https://developers.privacy.com/docs/api-basics), [D/docs/cards](https://developers.privacy.com/docs/cards) |

---

## 5. Операции: статусы, отказы, уведомления

**Статусы операции** ([D/docs/transactions](https://developers.privacy.com/docs/transactions)):
- `PENDING`: авторизация, ждём продавца
- `SETTLING`: продавец завершил, списываем с источника
- `SETTLED`: завершена
- `VOIDED`: продавец отменил авторизацию
- `DECLINED`: отклонена
- `BOUNCED`: не удалось списать с источника (API-аккаунт могут отключить)

**События внутри операции:** `AUTHORIZATION`, `AUTHORIZATION_ADVICE` (отказ выше по цепочке или изменение суммы), `CLEARING`, `VOID`, `RETURN` (возврат на карту). Хранятся сумма авторизации, сумма расчёта, сумма в валюте продавца и `acquirer_fee`. Продавец: `descriptor`, `mcc`, город, штат, страна, `acceptor_id`. В `funding` указано, из чего оплачено, включая `PROMO` (кредиты). Есть 6-значный `authorization_code`.

**Причины отказа (полный список из API):**

| Код | Смысл | Для экрана «Шлюза» простыми словами |
|---|---|---|
| `CARD_PAUSED` | карта на паузе | «Карта на паузе — не пустили» |
| `CARD_CLOSED` | карта закрыта | «Карта закрыта» |
| `UNAUTHORIZED_MERCHANT` | привязанная карта, чужой магазин | «Это не тот сервис — карта работает только в Иви» |
| `SINGLE_USE_RECHARGED` | одноразовую пытаются списать второй раз | «Одноразовая карта уже использована» |
| `USER_TRANSACTION_LIMIT` | превышен лимит пользователя | «Больше твоего предела» |
| `GLOBAL_TRANSACTION_LIMIT` / `GLOBAL_WEEKLY_LIMIT` / `GLOBAL_MONTHLY_LIMIT` | превышен лимит платформы на аккаунт | «Ты дошёл до общего предела Шлюза на сутки / неделю / месяц» |
| `INSUFFICIENT_FUNDS` | нет денег на источнике | «На Шлюзе не хватило денег» |
| `INSUFFICIENT_FUNDS_PRELOAD` | ответ системы клиента (ASA) | — |
| `BANK_CONNECTION_ERROR` | источник отвалился, переподключить | «Карта для пополнения отключилась — подключи заново» |
| `BANK_NOT_VERIFIED` | источник не подтверждён | «Карта для пополнения ещё не подтверждена» |
| `INVALID_CARD_DETAILS` | неверный CVV или срок | «Сервис ввёл неверный код или срок — проверь цифры» |
| `INCORRECT_PIN` | неверный PIN | — |
| `FRAUD_ADVICE` | отказ по риску | «Похоже на мошенничество — не пустили» |
| `MERCHANT_BLACKLIST` | продавец запрещён на платформе | «Здесь картами Шлюза платить нельзя» |
| `ACCOUNT_STATE_TRANSACTION_FAIL`, `INACTIVE_ACCOUNT` | проблема с аккаунтом, обратиться в поддержку | «Напиши нам — разберёмся» |
| `SWITCH_INOPERATIVE_ADVICE`, `UNKNOWN_HOST_TIMEOUT` | сбой сети, повторить | «Сбой связи — сервис может попробовать ещё раз» |
| `APPROVED` | одобрено | — |

В справке есть страница со списком отказов человеческим языком: «Card was paused at time of transaction — не забудь снять паузу», «проверь CVV и срок», «если магазин сам отклоняет — пиши магазину». Нет отказа в списке — писать на support@privacy.com. [S/360041447214](https://support.privacy.com/hc/en-us/articles/360041447214-Why-was-a-transaction-declined-when-I-tried-to-use-a-Privacy-Card) (по выдаче)

**Уведомления:**
- О каждой операции: пуш и/или email, «в реальном времени». [P/business](https://www.privacy.com/business), [P/unique-card-number](https://www.privacy.com/unique-card-number)
- Об отказе: по лимиту ([P/spend-limits](https://www.privacy.com/spend-limits)), по повторному списанию одноразовой ([P/single-use-cards](https://www.privacy.com/single-use-cards))
- Чек письмом по пакетному списанию ([S/25915302975383](https://support.privacy.com/hc/en-us/articles/25915302975383-What-is-this-Transaction-Receipt-email), по выдаче). Подтверждение операции считается чеком ([P/terms](https://www.privacy.com/terms) §3)
- Сервисные SMS, звонки и автодозвон про счёт (не реклама), фрод-алерты и hold-алерты на email ([P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §11)
- Если не дать разрешение на пуши, приложение всё равно работает. От маркетинговых писем можно отписаться, сервисные приходят всё равно ([P/privacy-policy](https://www.privacy.com/privacy-policy))
- Вебхуки (API): POST на каждое событие с подписью HMAC-SHA256 в `X-Privacy-HMAC`. Повторы с экспоненциальной задержкой: первый через 5 мин, до 24 ч. Только для отчётности, решать об авторизации через них нельзя. Отказы в вебхуках есть только у Issuing-аккаунтов. [D/docs/transaction-webhooks](https://developers.privacy.com/docs/transaction-webhooks)

---

## 6. Возвраты и споры

**Возврат от продавца:**
- Возврат всегда идёт **на исходный источник денег**, даже если карта на паузе или закрыта. Срок 3–5 рабочих дней с момента, когда продавец или Privacy инициировал возврат. [S/360012285954](https://support.privacy.com/hc/en-us/articles/360012285954), [S/7971551107479](https://support.privacy.com/hc/en-us/articles/7971551107479-How-do-refunds-for-disputes-work) (по выдаче)
- Отменённая или истёкшая авторизация не порождает возврата: деньги и не списывались. [S/7971048299927](https://support.privacy.com/hc/en-us/articles/7971048299927-A-merchant-said-they-canceled-my-order-why-haven-t-I-received-a-refund) (по выдаче)
- Комиссия 3% за зарубежную операцию **при возврате не возвращается**. [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §6a

**Спор (чарджбэк) — по шагам:**
1. Сначала написать продавцу: часто так быстрее. [блог: процесс споров](https://www.privacy.com/blog/the-payment-dispute-resolution-process)
2. В приложении или в вебе выбрать операцию → «Dispute Transaction» внизу окна. По `PENDING` нельзя, только `SETTLING` или `SETTLED`. [S/8581108676119](https://support.privacy.com/hc/en-us/articles/8581108676119-How-do-I-submit-a-dispute-for-a-transaction-I-made-using-Privacy) (по выдаче); из приложения — с редизайна ([блог](https://www.privacy.com/blog/introducing-redesigned-privacy-mobile-app-for-ios-android))
3. Приложить доказательства. Если их нет, агент пишет письмо и просит. Потом спор уходит в платёжную систему. (по выдаче)
4. Возможен **временный возврат (provisional credit)** на время разбирательства. Права — изнутри Privacy: решение в пользу клиента делает его постоянным, против — сторнирует. (по выдаче, [S/7971551107479](https://support.privacy.com/hc/en-us/articles/7971551107479-How-do-refunds-for-disputes-work))
5. Этапы платёжной системы: First Chargeback (у продавца 30–45 дней на ответ) → Second Presentment (у банка 30–45 дней) → Pre-arbitration → арбитраж платёжной системы. [блог: процесс споров](https://www.privacy.com/blog/the-payment-dispute-resolution-process)
6. Отменённый спор можно переоткрыть письмом в support, пока не истёк срок чарджбэка. [S/8581248432535](https://support.privacy.com/hc/en-us/articles/8581248432535-Why-was-my-dispute-canceled) (по выдаче)
7. **Не открывать спор через свой банк:** это **замораживает аккаунт Privacy**, после расчёта его размораживают и просят подать спор в Privacy. [S/8581346759063](https://support.privacy.com/hc/en-us/articles/8581346759063-Should-I-open-a-dispute-with-my-bank) (по выдаче)

**Сроки:**
- В Privacy: **90 календарных дней** с даты завершения операции для большинства случаев. [S/8581043595031](https://support.privacy.com/hc/en-us/articles/8581043595031-How-long-do-I-have-to-file-a-dispute) (по выдаче)
- По договору (ошибка в выписке): написать **в течение 60 дней** после выписки, письменно или в приложении (звонок не считается). Подтверждение — **за 30 дней**, решение — **за 90 дней**. Пока идёт разбор, долг не взыскивают и о просрочке не сообщают, но Available Credit могут уменьшить. Если правила нарушены, первые $50 спорной суммы можно не платить. Не согласен с ответом — написать в течение 10 дней. Претензия к товару: покупка дороже $50, в своём штате или в пределах 100 миль, ещё не оплачена. [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §9
- Остановить автоплатёж по спорной сумме: за 3 рабочих дня. [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §9
- Весь процесс до 90 дней, иногда дольше. Окна платёжных систем: обычно 120 дней, «неавторизованные» 60 дней, «не получил товар» 120–540 дней. [блог: процесс споров](https://www.privacy.com/blog/the-payment-dispute-resolution-process)
- Бизнес-счета: Reg E не действует, спорную сумму советуют оплатить до решения, Program Manager решает «коммерчески разумно». [P/commercial-cardholder-agreement](https://www.privacy.com/commercial-cardholder-agreement) §9
- После возмещения клиент передаёт банку права требования к продавцу и помогает документами. [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §9

---

## 7. Тарифы

Источник: [P/pricing](https://www.privacy.com/pricing), [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) (Annual Fee).

| | **Personal** | **Plus** «Recommended» | **Pro** | **Premium** «Best for Small Businesses» |
|---|---|---|---|---|
| Цена в месяц | $0 | $5 | $10 | $25 |
| Цена за год (оплата раз в год) | — | $60 | $120 | $300 |
| Новых карт в месяц | 12 | 24 | 36 | 60 |
| Merchant-Locked, Single-Use | ✓ | ✓ | ✓ | ✓ |
| Лимиты (операция, месяц, год, всего) | ✓ | ✓ | ✓ | ✓ |
| Пауза и закрытие | ✓ | ✓ | ✓ | ✓ |
| Category-Locked | — | ✓ | ✓ | ✓ |
| Card Sharing | — | ✓ | ✓ | ✓ |
| Card Notes | — | ✓ | ✓ | ✓ |
| API (а значит, MCP) | — | ✓ | ✓ | ✓ |
| Приоритетная поддержка и чат (по блогу) | — | ✓ | ✓ | ✓ |
| Everywhere Cards (до 3) | — | — | ✓ | ✓ |
| Кэшбэк 1% до $4 500 в месяц | — | — | ✓ | ✓ |
| Комиссия за зарубежные операции | 3%, мин. $0,50 | 3%, мин. $0,50 | 0 | 0 |

- Внутри страны операции бесплатны на всех тарифах. Пополнение банком или картой без комиссии, но «могут ввести». [P/terms](https://www.privacy.com/terms) §7
- Подписка списывается в день оформления и затем в то же число каждый месяц (до 14.11.2025 — 1-го числа). Повышение тарифа: остаток текущего периода засчитывается пропорционально. Отмена до даты списания; доступ сохраняется до конца оплаченного периода, деньги не возвращаются. Цену меняют с уведомлением **за 30 дней**. Тариф меняют в веб-версии: «Account → Change Plan». [P/terms](https://www.privacy.com/terms) §7, [блог Plus](https://www.privacy.com/blog/introducing-privacy-plus-plan)
- Нужно больше карт и есть зарегистрированный бизнес — писать в support. [P/pricing](https://www.privacy.com/pricing)
- История: в 2019 году были Pro ($10), Teams (цена в посте не указана), Issuing (API за $0,25 за карту, 250 бесплатно). Ранних пользователей оставили на старых условиях. [блог 2019](https://www.privacy.com/blog/subscription-plan)

---

## 8. Договор держателя карты, Terms, Privacy Policy

### Комиссии
- Зарубежные операции: max(3%, $0,50) на Personal и Plus, при возврате не возвращается. Абонплата: $0 / $60 / $120 / $300 в год, оплата помесячно. Конвертацию валюты делает платёжная система, курс на дату расчёта. [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement), [P/terms](https://www.privacy.com/terms) §18
- Банк вправе списывать комиссии и расходы (юристы, исполнение судебных актов) с Secured Account и внешнего счёта **без уведомления**. [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §13 i, n, o

### Ответственность
- **Ответственность Privacy ограничена** большим из двух: комиссии клиента за 3 месяца или **$5**. За взлом и несанкционированный доступ к аккаунту Privacy не отвечает. Сервис «as is». [P/terms](https://www.privacy.com/terms) §14–15
- Клиент отвечает за всё в аккаунте, включая действия тех, кому дал доступ или карту. Передал пароль — нарушение договора и полная ответственность. [P/terms](https://www.privacy.com/terms) §1, §18; [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §13 a
- Спорные покупки: качество товара — с продавцом, кроме прав из §9. [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §9
- Залог: банк держит первоочередной залог на Secured Account и списывает его при дефолте или закрытии **без уведомления**. Есть право зачёта по любым счетам клиента у Privacy. [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §8, [P/terms](https://www.privacy.com/terms) §16
- Арбитраж AAA, только индивидуальный (без коллективных исков, без суда присяжных). Малые иски можно подавать в суд. Перед арбитражем — письменная претензия и 60 дней. Сроки подачи: по Terms **90 дней** с возникновения спора, по договору с банком 2 года. Право: Terms — Нью-Йорк, договор — Коннектикут. [P/terms](https://www.privacy.com/terms) §17, [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §13 r–s и Arbitration

### Блокировки и закрытие
- **Дефолт:** не оплатил вовремя, платёж вернулся, превысил лимит, **дал кому-то логин**, банкротство, смерть или недееспособность, ложные сведения, **отозвал согласие на электронные документы**, нарушил договор, незаконная покупка, **переехал из США**, арест счёта. Последствия без уведомления: закрыть карты или аккаунт, снизить лимит, потребовать всё сразу, суд за счёт клиента. [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §10
- **Банк может отклонять, замораживать, задерживать операции** при: выезде за пределы США, судебном разбирательстве, противоречивых сведениях о владельце, **подозрении, что клиента обманывают (даже если он сам подтвердил)**, подозрении на отмывание или фрод, санкционных проверках, риске потерь. [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §12 d
- **Privacy может** закрыть аккаунт «в любое время, по любой причине или без причины», с уведомлением или без. После закрытия данные могут удалить, компенсаций нет. При отрицательном балансе удерживают возвраты и списывают с источника. При «чрезмерных» спорах и ошибках вводят особые условия или блокируют. [P/terms](https://www.privacy.com/terms) §9, §18; [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §12 b
- **Ограничение на время расследования** или по требованию госорганов. При подозрении на незаконное использование данные передаются в правоохранительные органы и партнёрам. В споре о владении аккаунтом Privacy «единственный арбитр». [P/terms](https://www.privacy.com/terms) §4–5
- Могут запросить документы в любой момент (паспорт, права, лицензию бизнеса). Отказ ведёт к блокировке. [P/terms](https://www.privacy.com/terms) §1
- **Клиент закрывает сам:** на сайте внизу страницы Account, в приложении Account Details → «Close My Account». Нельзя при операциях в обработке, нерасчитанных операциях или открытых спорах. По договору: при долге счёт ограничивают до погашения. [S/360013720233](https://support.privacy.com/hc/en-us/articles/360013720233-How-do-I-close-my-Privacy-Account) (по выдаче), [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §12 a; по Terms — письмом в support ([P/terms](https://www.privacy.com/terms) §9)
- Банк-эмитент может смениться с предварительным уведомлением. Условия меняются: новая версия действует с публикации, продолжение пользования = согласие. [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §13 g–h, [P/terms](https://www.privacy.com/terms) §18
- Неактивные счета: могут не исполнять операции до подтверждения личности. Умер или признан недееспособным — операции исполняют до 10 дней. [P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §13 d, k

### Данные: что собирают, зачем, кому передают
- **Собирают:** имя, email, телефон, дату рождения, гос. ID-номер, данные карт и банка; данные операций (когда, где, как, с какого устройства); данные устройства (модель, ОС, идентификаторы, мобильная сеть, браузер, IP); cookies; данные от сервисов проверки личности, из открытых источников и бюро. По CCPA также геолокация (по IP), записи звонков, «выводы о предпочтениях». [P/privacy-policy](https://www.privacy.com/privacy-policy), [P/california-consumer-privacy-act-notice](https://www.privacy.com/california-consumer-privacy-act-notice)
- **Зачем:** проверка личности, защита, работа сервиса. **Данные передаются продавцу, если клиент открыл с ним спор.** По CCPA также «персонализация, реклама и маркетинг своих продуктов». [там же]
- **Кому передают:** подрядчикам, банкам, процессорам, платёжным системам, госорганам (по закону или запросу), при сделке M&A, с согласия клиента. Агрегированные анонимные данные — кому угодно. «Не продаём и не shared в смысле CCPA». [там же]
- **Apple Pay:** передаются имя и фамилия, email в замаскированном виде, последние 4 цифры. Не передаются полный телефон, адрес, история операций. [блог: Apple/Google Pay](https://www.privacy.com/blog/a-guide-to-securely-using-privacy-cards-with-apple-pay-and-google-pay)
- **Byline Bank** делится данными для своих операций, своего маркетинга и операций аффилированных компаний, ограничить это нельзя. Не делится для маркетинга третьих лиц. [P/byline-privacy-policy](https://www.privacy.com/byline-privacy-policy)
- **Хранение после закрытия:** данные проверки личности 5 лет, данные карт 5 лет, источник денег (банк) 6 лет, журналы аудита 3 года с создания, ACH-операции 6 лет. [P/privacy-policy](https://www.privacy.com/privacy-policy)
- **Права клиента:** исправить данные в аккаунте; отписаться от рекламы. CCPA: узнать, удалить, исправить — ответ о получении за 10 рабочих дней, по существу за 45 дней. Do Not Track не учитывается. Cookies: необходимые, аналитика, маркетинг; последние две можно выключить в баннере. [P/privacy-policy](https://www.privacy.com/privacy-policy), [P/california-consumer-privacy-act-notice](https://www.privacy.com/california-consumer-privacy-act-notice)
- **ИИ:** «данные карт и операций в ИИ-модели не передаём», подключение к ИИ — только по выбору клиента через MCP. [P/ai](https://www.privacy.com/ai)
- **Контент и идеи** клиента Privacy может использовать бесплатно и без ограничений. [P/terms](https://www.privacy.com/terms) §8, §11

---

## 9. Безопасность

- Сертификации: PCI-DSS, SOC 1 и SOC 2 Type 2, ISO 27001. Ежегодные сертификационные проверки. [P/security](https://www.privacy.com/security), [P/privacy-policy](https://www.privacy.com/privacy-policy)
- Пароли: PBKDF2, 100 тыс. итераций, соль. Чувствительные данные шифруются, данные хранятся в географически разнесённых ЦОДах (AWS плюс выделенное железо). [P/security](https://www.privacy.com/security)
- Передача: только TLS с HSTS. Между ЦОДами IPsec с AES-256. На маркетинговых страницах: «256-bit encryption». [P/security](https://www.privacy.com/security), [P/](https://www.privacy.com)
- Процессы: ротация ключей шифрования **дважды в год**, firewall, патчи, OWASP, ревью всего кода, принцип наименьших привилегий. MFA обязательна для **всех сотрудников** (в Privacy Policy: «for all users»). [P/security](https://www.privacy.com/security), [P/privacy-policy](https://www.privacy.com/privacy-policy)
- Для клиента: 2FA по TOTP; банковский логин хранит Plaid, не Privacy. [блог о безопасности](https://www.privacy.com/blog/is-privacy-com-safe-an-overview-of-privacys-security-practices)
- Продуктовая защита: привязка к магазину, одноразовость, лимиты, пауза, уведомления; в кошельках телефона токенизация и Secure Element. Автопауза через год простоя. Разбор атак перебором номеров (PAN enumeration) есть в блоге (не читали подробно).
- Программа сообщений об уязвимостях: vdp@privacy.com. В области действия api, demo и sandbox.privacy.com. Не принимаются DoS, фишинг, social engineering, self-XSS, спам, rate-limit на неавторизационных точках. 90 дней до публикации, Safe Harbor. [P/legal/security](https://www.privacy.com/legal/security)
- API: секретный ключ в заголовке `Authorization`; ограничения по частоте запросов и по перебору ключей с одного IP; вебхуки с HMAC. Создание «unlocked» карт через API — отдельное право по запросу. [D/docs/api-basics](https://developers.privacy.com/docs/api-basics)
- Открытие номера и CVV в приложении — подробностей на сайте нет. В API PAN и CVV возвращаются только в ответе по одной карте. [D/docs/cards](https://developers.privacy.com/docs/cards)

---

## 10. Расширение и приложение

**Браузерное расширение** — Chrome, Safari (macOS и iOS), Firefox, Edge. [P/browser-extension](https://www.privacy.com/browser-extension)
- Само заполняет номер, срок и CVV на оплате.
- **Подсказывает карты из кошелька по сайту**, на котором ты сейчас.
- Создаёт новую карту прямо на странице оплаты.
- Можно «приколоть» карту в угол сайта и копировать поля по одному. Видны лимиты карты и аккаунта, есть тёмная тема. [блог: расширение 2023](https://www.privacy.com/blog/faster-easier-checkout-with-the-new-privacy-browser-extension)
- Список операций, вход упрощён, лучше уживается с менеджерами паролей, значок «P» в поле оплаты. [блог: обновление окт. 2023](https://www.privacy.com/blog/product-update-browser-extension-oct-2023)
- На iOS (Safari, iOS 15+): включается через «aA → Manage Extensions», нужно «Always Allow on Every Website». Значок «P» внизу слева открывает выбор или создание карты. [блог iOS](https://www.privacy.com/blog/product-update-ios-extension-oct-2023)
- Связка с 1Password: создание карт Privacy из 1Password. [блог 1Password](https://www.privacy.com/blog/create-virtual-cards-with-privacy-and-1password) (детали не разбирали)

**Мобильное приложение** — iOS, iPadOS, Android. [P/mobile-app](https://www.privacy.com/mobile-app), [блог: новое приложение](https://www.privacy.com/blog/introducing-redesigned-privacy-mobile-app-for-ios-android)
- Вкладки Wallet · Activity · Account. Светлая и тёмная тема, можно как в системе.
- Создать карту «за секунды»; пауза и закрытие откуда угодно.
- Свайп вправо: в избранное, пауза или снятие паузы. Избранные сверху.
- Цвет и эмодзи карты.
- Сортировка и фильтры карт, поиск по операциям.
- Пуш-уведомления, синхронизация между устройствами.
- Спор по операции прямо из приложения.
- Добавить Everywhere-карту в Apple, Google или Samsung Wallet (push provisioning).

Также есть **веб-приложение** app.privacy.com: там смена тарифа, API-ключ и вебхуки.

---

## 11. Чего нет в прототипе «Шлюза» и что добавить

**Что уже есть в `index.html`:** кошелёк с пополнением (СБП или карта) и автопополнением под списание; карта на подписку (только этот сервис), на категорию, одноразовая с датой конца пробного периода; включить, выключить, пауза на неделю или до 1-го числа; лимиты за сутки, за раз, за месяц, за всё время; «Пропустить один раз» при превышении; лента «Что было» с группировкой отказов и суммой «не пустили»; «в обработке» → «проведено»; проверка карты на 1 ₽; возврат на Шлюз даже при закрытой карте; заявка «Не узнаю это списание» с причинами и этапами (сервис → банк → временный возврат → решено), карта на паузе на время спора; заметка; «Кто пользуется» (семья); показ номера по лицу, копирование полей; удаление с закрытием карты; три уведомления (о каждом списании, когда не пустили, за день до); тарифы с лимитом подписок и одноразовых карт; вход по SMS, проверка через Госуслуги, выбор источника; знакомство из 4 экранов.

**Приоритетный список «что добавить»** (формулировки — для экрана):

**P1 — без этого продукт выглядит недоделанным рядом с Privacy**
1. **Человеческие причины отказа** во всех событиях «не пустили», по полному списку из разд. 5. Сейчас у нас только «выключена / пауза / предел / нет денег». Добавить: «Это не тот сервис — карта работает только в Иви», «Одноразовая карта уже использована», «Сервис ввёл неверный код или срок», «Похоже на мошенничество — не пустили», «Сбой связи — сервис может попробовать ещё раз», «Ты дошёл до общего предела Шлюза на сегодня». ([D/docs/transactions](https://developers.privacy.com/docs/transactions))
2. **Привязка к сервису по первой оплате.** Сейчас карта «только для Иви» по выбору из списка, а в жизни её нужно привязывать к тому, кто первым списал. Экран: «Карта привязалась к Иви при первой оплате 3 ноября / В других местах не сработает». Для «своей» подписки: «Ждём первое списание — к нему и привяжем карту». ([D/docs/cards](https://developers.privacy.com/docs/cards))
3. **Общий предел аккаунта и экран «Сколько ещё можно»:** «За сутки потрачено 1 200 ₽ из 15 000 ₽ / За месяц 4 300 ₽ из 50 000 ₽». Плюс «Как поднять предел». Это требование банка и антифрода, у Privacy он есть всегда. ([S/360012405933](https://support.privacy.com/hc/en-us/articles/360012405933-How-much-can-I-spend-using-Privacy), по выдаче)
4. **Правила спора по-честному:** срок «Оспорить можно в течение 90 дней после списания»; по операции «в обработке» кнопку не показывать («Спорить можно, когда списание проведено»); шаг «Приложи скриншот или письмо от сервиса — так быстрее»; в конце «Деньги вернутся на Шлюз за 3–5 дней». Отдельно предупредить: «Не спорь через свой банк — так заморозится весь Шлюз». ([разд. 6](#6-возвраты-и-споры))
5. **Срок карты и перевыпуск.** Сейчас срок генерируется, а что будет, когда он кончится, не показано. Нужно: за 30 дней «Карта Okko кончается в марте / Выпустить новую и вставить в Okko»; автопауза забытых карт — «Карта не работала год — поставили на паузу / Включить можно в один нажим». ([S/7970204090647](https://support.privacy.com/hc/en-us/articles/7970204090647-What-happens-when-a-Privacy-Card-expires), [S/20321316268439](https://support.privacy.com/hc/en-us/articles/20321316268439-Why-was-my-Privacy-Card-paused-without-my-knowledge), по выдаче)
6. **Закрыть Шлюз и забрать деньги.** Экран «Закрыть Шлюз»: «Сначала дождёмся списаний в обработке и закончим споры / Остаток 650 ₽ вернём на карту Т-Банк •• 1234». Плюс что храним после закрытия и сколько лет: «По закону храним данные о тебе 5 лет». ([P/privacy-policy](https://www.privacy.com/privacy-policy))
7. **Возврат после закрытой карты — с суммой и ожиданием.** У нас уже «Лежат на Шлюзе». Добавить «Сервис обещал вернуть? Деньги придут за 3–5 дней. Не пришли — напиши нам». ([S/360012285954](https://support.privacy.com/hc/en-us/articles/360012285954), по выдаче)

**P2 — сильные отличия Privacy, которые подходят «Шлюзу»**

8. **Скрытые покупки в выписке банка** (Private Spend Mode): «В выписке твоего банка будет только «Шлюз» — без названий сервисов». У нас это и так выходит из модели кошелька, но об этом нужно сказать как о выгоде в знакомстве или настройках. ([P/private-and-discreet-payments](https://www.privacy.com/private-and-discreet-payments))
9. **Оформление и порядок в списке:** цвет и значок карты, «Закрепить сверху» (избранное), свайп «пауза / включить» прямо в списке, поиск по истории («Найти списание»), фильтры «Только включённые / На паузе / Одноразовые». ([блог: приложение](https://www.privacy.com/blog/introducing-redesigned-privacy-mobile-app-for-ios-android))
10. **Делиться картой ссылкой**, а не только внутри семьи: «Отправить карту по ссылке / Ссылка работает 24 часа, а включать и выключать можешь только ты». ([D/reference/share](https://developers.privacy.com/reference/post_cards-card-token-share))
11. **Лимит за год и за неделю** в «Сколько можно списывать» — для годовых подписок («За год — до 2 990 ₽») и категорий («На доставку — до 3 000 ₽ в неделю»). ([P/spend-limits](https://www.privacy.com/spend-limits))
12. **Уведомление о повторной попытке одноразовой карты:** «Литрес снова пытался списать 399 ₽ — карта одноразовая, не пустили / Нравится сервис — подключи постоянную карту». ([P/single-use-cards](https://www.privacy.com/single-use-cards))
13. **Расширение для браузера и подсказка карты по сайту:** «Ты на сайте Okko — подставить карту Шлюза?» и «Новая карта для этого сайта». Для мобильного Safari — тот же значок в поле оплаты. ([P/browser-extension](https://www.privacy.com/browser-extension))
14. **Вход с одноразовым кодом из приложения-аутентификатора** (2FA) в профиле: «Вход по коду из приложения-ключа — даже если украдут СМС, не зайдут». ([блог о безопасности](https://www.privacy.com/blog/is-privacy-com-safe-an-overview-of-privacys-security-practices))
15. **Тариф: честная смена и отмена.** «Отменить можно в любой момент — тариф работает до 3 декабря, деньги за этот месяц не возвращаем», «Перешёл на больший тариф — оставшиеся дни засчитаем», «Цену меняем с предупреждением за 30 дней». ([P/terms](https://www.privacy.com/terms) §7)

**P3 — позже, если решат**

16. **Карта для оплаты телефоном в магазине** (у нас — Mir Pay или СБП-аналог; у Privacy — Everywhere, только на дорогих тарифах и не больше 3): «Карта для магазинов — работает везде, где можно оплатить телефоном». ([P/everywhere-cards](https://www.privacy.com/everywhere-cards))
17. **Кэшбэк на старшем тарифе:** «1% с подписок возвращаем на Шлюз — до 450 ₽ в месяц», начисление до 10-го числа. ([P/terms](https://www.privacy.com/terms) §2)
18. **Пригласи друга:** «Тебе и другу по 300 ₽ на Шлюз после его первой оплаты». ([P/terms](https://www.privacy.com/terms) §2)
19. **Выписка за период и чек письмом:** «Скачать выписку за октябрь», «Чек по каждому пополнению — на почту». ([P/cardholder-agreement](https://www.privacy.com/cardholder-agreement) §2h)
20. **ИИ-помощник или API** — только по выбору клиента: «Подключить Шлюз к своему ИИ-помощнику / Мы сами твои данные в ИИ не отдаём». ([P/ai](https://www.privacy.com/ai))
21. **Запрет ставок и переводов на карты Шлюза** — сказать заранее, а не узнавать по отказу: «Картами Шлюза нельзя платить за ставки, лотереи, переводы и пополнение других карт». ([P/terms](https://www.privacy.com/terms) §4)

**Отличия моделей, которые нужно учесть (не функции):**
- У Privacy денег на счету нет: каждое списание сразу тянется с банка клиента, а сам он — кредитная карта банка. У нас кошелёк, значит другой юридический тип (предоплаченная карта или электронный кошелёк) и вопрос, чей остаток. Это нужно решить с банком-партнёром до текста договора.
- Privacy держит спор у себя и просит не идти в свой банк. У нас пополнение по СБП или картой не связано с конкретным списанием, поэтому спор через банк клиента ничего не вернёт — стоит прямо написать «Оспаривай через Шлюз».
- В ACH и AutoPay Privacy заранее получает согласие списывать до $10 000 в день без уведомлений. Наше «автопополнение под списание» — аналог: нужен явный текст согласия и потолок суммы («Автопополнение — не больше 5 000 ₽ в день»).

---

### Посты блога про механику продукта (последние три только скачаны и пролистаны, в опись почти не вошли)
[Plus](https://www.privacy.com/blog/introducing-privacy-plus-plan) · [Everywhere](https://www.privacy.com/blog/introducing-privacy-everywhere-cards) · [новое приложение](https://www.privacy.com/blog/introducing-redesigned-privacy-mobile-app-for-ios-android) · [расширение 2023](https://www.privacy.com/blog/faster-easier-checkout-with-the-new-privacy-browser-extension) · [обновление расширения](https://www.privacy.com/blog/product-update-browser-extension-oct-2023) · [iOS-расширение](https://www.privacy.com/blog/product-update-ios-extension-oct-2023) · [Apple и Google Pay](https://www.privacy.com/blog/a-guide-to-securely-using-privacy-cards-with-apple-pay-and-google-pay) · [MCP](https://www.privacy.com/blog/privacy-mcp-connect-ai-assistant-privacy-account) · [API для агентов](https://www.privacy.com/blog/privacy-api-agentic-workflow) · [Issuing API](https://www.privacy.com/blog/introducing-the-privacy-card-issuing-api) · [безопасность](https://www.privacy.com/blog/is-privacy-com-safe-an-overview-of-privacys-security-practices) · [Privacy → Lithic](https://www.privacy.com/blog/our-journey-from-privacy-com-to-lithic) · [тарифы 2019](https://www.privacy.com/blog/subscription-plan) · [процесс споров](https://www.privacy.com/blog/the-payment-dispute-resolution-process) · [OpenClaw](https://www.privacy.com/blog/openclaw-ai-agent-spending-virtual-card) · [1Password](https://www.privacy.com/blog/create-virtual-cards-with-privacy-and-1password) · [как пользоваться картой](https://www.privacy.com/blog/how-to-use-a-virtual-card) · [спор по подписке](https://www.privacy.com/blog/can-you-dispute-a-subscription-charge)

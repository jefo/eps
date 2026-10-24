# Design SYstem v1 

Файлы навыка `gpt-image-2` приняты к сведению — **пока их не трогаем и откладываем до вашего сигнала**.

Ниже представлена **полная дизайн-система (Design System)**, снятая непосредственно с визуального языка референсного видео (стиль современного интерактивного технического эксплейнера / micro-learning лонгрида). 

Она спроектирована так, чтобы на ней можно было сверстать как адаптивный веб-лонгрид (HTML/Tailwind/CSS), так и интерактивные слайды визуального эссе.

---

# Дизайн-система: «Visual Explainer / Tech Essay»

## 1. Концепция и философия стиля
* **Жанр:** Чистый, минималистичный продуктово-инженерный эксплейнер (SaaS / Stripe-like / Visual Tech Essay).
* **Базовое ощущение:** Светлое пространство, «дышащий» интерфейс, фокус на одном шаге повествования за раз.
* **Главный визуальный приём:** Повествование через цепочку состояний (Pipeline Flow) и метафору интерфейсов (окно браузера, карточка заказа, логи терминала, бейджи технологий).

---

## 2. Цветовая палитра (Color Tokens)

### 2.1. Основные (Brand & Canvas)
| Токен | HEX | Назначение |
|---|---|---|
| `bg-canvas` | `#F8FAFC` | Общий фон страницы (сверхсветлый холодный slate) |
| `bg-surface` | `#FFFFFF` | Фон основных карточек, окон и панелей |
| `primary` | `#6366F1` / `#7C3AED` | Фирменный фиолетово-индиго акцент (кнопки, активные связи, фокус) |
| `primary-hover`| `#4F46E5` / `#6D28D9` | Состояние наведения/нажатия |
| `primary-subtle`| `#EEF2FF` / `#F5F3FF` | Фоновые плашки активных элементов, подсветка шагов |

### 2.2. Текстовые цвета
| Токен | HEX | Назначение |
|---|---|---|
| `text-primary` | `#0F172A` | Заголовки, ключевые термины, контрастный текст |
| `text-secondary` | `#475569` | Основной пояснительный текст, подписи |
| `text-muted` | `#94A3B8` | Плейсхолдеры, неактивные шаги, вторичные метки |
| `text-on-primary` | `#FFFFFF` | Текст на активных плашках и кнопках |

### 2.3. Семантические цвета (Технологии, статусы и диаграммы)
В референсе каждому типу сущности присвоен мягкий, но контрастный цвет:
* **Зеленый (Success / Verified / DB / Storage):** `#10B981` (фон бейджей: `#ECFDF5`)
* **Красный (Error / Rejected / High Load / Alert):** `#EF4444` (фон бейджей: `#FEF2F2`)
* **Синий (Services / Docker / Flow):** `#3B82F6` (фон бейджей: `#EFF6FF`)
* **Янтарный / Оранжевый (Queues / Warning / Kafka):** `#F59E0B` (фон бейджей: `#FFFBEB`)
* **Циан / Бирюза (Cache / Redis / Memory):** `#06B6D4` (фон бейджей: `#ECFEFF`)

---

## 3. Типографика

**Шрифт:** Геометрический гротеск без засечек с отличным рендерингом мелких деталей:
* *Рекомендуемые веб-шрифты:* `Plus Jakarta Sans`, `Inter`, `Poppins`, `SF Pro Display`.
* *Моноширинный шрифт (для путей, API и логов):* `JetBrains Mono`, `Fira Code`.

### Иерархия:
1. **Screen Title (H1):** `font-size: 32px` (mobile: 24px), `font-weight: 800` (ExtraBold), `letter-spacing: -0.02em`. С обязательной акцентной фиолетовой чертой-индикатором снизу (толщина 4px, ширина 40px, скругление 2px).
2. **Sub-heading / Step Number:** `font-size: 16px`, `font-weight: 700`, формат `01 Name`, цвет `primary`.
3. **Card Title (H2/H3):** `font-size: 20px - 22px`, `font-weight: 700`, `text-primary`.
4. **Body Text:** `font-size: 16px`, `line-height: 1.6`, `font-weight: 400 - 500`.
5. **Badge & UI Label:** `font-size: 12px - 14px`, `font-weight: 600`, `letter-spacing: 0.01em`.
6. **Code / Endpoint:** `font-family: monospace`, `font-size: 13px`, `padding: 2px 6px`, фон `#F1F5F9`.

---

## 4. Сетка, скругления и тени (Elevation & Radii)

### 4.1. Скругления (Border Radius)
* `rounded-sm`: `6px` — теги, бейджи статуса, чекбоксы.
* `rounded-md`: `12px` — маленькие иконки технологий, поля ввода.
* `rounded-lg`: `16px` — кнопки действий (CTA), стандартные карточки.
* `rounded-xl`: `24px` — большие контейнеры экранов, модальные окна, макеты браузера.
* `rounded-full`: `9999px` — круги таймлайна, плавающие пиллы (Pill-buttons).

### 4.2. Тени (Soft Shadows)
Вместо резких контуров используется мягкое рассеивание света:
* `shadow-card`: `0px 10px 30px -5px rgba(15, 23, 42, 0.05), 0px 4px 10px -2px rgba(15, 23, 42, 0.03)`
* `shadow-hover`: `0px 20px 40px -10px rgba(15, 23, 42, 0.1)`
* `shadow-button`: `0px 8px 20px -4px rgba(99, 102, 241, 0.4)` (цветная тень в тон кнопки)
* `border-subtle`: `1px solid #E2E8F0` (очень тонкая деликатная рамка).

---

## 5. Базовые компоненты (UI Kit)

### 5.1. Заголовочный блок экрана (Header Block)
```html
<!-- Конструкция заголовка как в видео -->
<div class="mb-8">
  <span class="inline-block px-3 py-1 mb-2 text-xs font-bold text-indigo-600 bg-indigo-50 rounded-full">01 Reverse proxy</span>
  <h2 class="text-3xl font-extrabold text-slate-900 tracking-tight">Reverse proxy</h2>
  <div class="w-10 h-1 bg-indigo-600 rounded-full mt-2"></div>
</div>
```

### 5.2. Карточка технологии / Узел (Tech Node Tile)
Белая карточка с иконкой и мягким скруглением:
* Размер: `56x56px` (компактный) или `72x72px` (акцентный).
* Фон: `#FFFFFF`, рамка: `1px solid #E2E8F0`, скругление: `16px`.
* Внутри: официальная SVG-иконка технологии (Nginx, Redis, Docker, Spring, etc.) по центру.

### 5.3. Интерактивная лента шагов (Horizontal Pipeline / Timeline)
* Горизонтальная направляющая серая линия (`#E2E8F0`, толщина `2px`).
* Узлы: круглые точки (`16px`), заполняющиеся акцентным цветом по мере прохождения запроса.
* Активный узел: фиолетовый с кольцом (`ring-4 ring-indigo-100`).

### 5.4. Статусные бейджи (Status Pills)
* **Verified:** Зеленый фон (`#ECFDF5`), зеленый текст (`#059669`), иконка галочки.
* **Rejected:** Красный фон (`#FEF2F2`), красный текст (`#DC2626`), иконка крестика.
* **Cached / Hit:** Циановый фон (`#ECFEFF`), текст (`#0891B2`).

### 5.5. Карточка-макет окна (Browser / App Mockup Window)
* Белый контейнер со скруглением `20px` и легкой тенью.
* В верхней части — «светофор» окна: три аккуратные серые или цветные точки (`#EF4444`, `#F59E0B`, `#10B981`) диаметром `8px`.
* Справа сверху — статусная метка (`LIVE`, `MOCKUP`).

### 5.6. Очередь сообщений (Message Queue Strip)
* Горизонтальный контейнер с полукруглым завершением или рамкой.
* Внутри последовательно идут цветные конверты/сообщения (Message Items), двигающиеся слева направо.

---

## 6. Шаблоны экранов визуального эссе (Layout Archetypes)

На основе видео выделяются **5 ключевых компоновок экрана**:

1. **«The Pipeline View» (Пошаговый конвейер запроса):**
   * Верх: Заголовок шага + контекст.
   * Центр: Длинная горизонтальная цепочка, где текущий шаг подсвечен карточкой-нодой, а остальные шаги приглушены.
   * Низ: Детализированная плашка (Что происходит: *Nginx перенаправляет трафик*).

2. **«The Comparison / Split Card» (Сравнение «Было/Стало» или «No vs Yes»):**
   * Две колонки. 
   * Левая: антипаттерн (например, запрос напрямую в БД без кеша — индикатор `Slow`).
   * Правая: правильный паттерн (запрос через Redis — индикатор `Fast`).

3. **«The Terminal Log» (Журнал вызовов):**
   * Окно темного или матового светло-серого цвета.
   * Строки формата: `[GET] /products/laptop`, `[POST] /orders`.
   * Подсветка повторяющихся запросов желтыми плашками.

4. **«The Interactive Architecture Tree» (Архитектурное дерево):**
   * Сверху пользователь (`User`), по центру микросервис бэкенда (`Backend API`), внизу параллельно подключенные зависимости: БД (`Postgres`), Кеш (`Redis`), Очередь (`Kafka`).

5. **«The Metric Gauge» (Дашборд здоровья):**
   * Карточка графиков: линия отклика (зеленая/красная), шкалы загрузки памяти и CPU, статус сервисов.

---

## 7. Готовый стартовый CSS/Tailwind конфиг для верстки

Если вы будете верстать это на Tailwind CSS, базовые токены настраиваются следующим образом:

```javascript
// tailwind.config.js (пресет для верстки экранов)
module.exports = {
  theme: {
    extend: {
      colors: {
        canvas: '#F8FAFC',
        surface: '#FFFFFF',
        brand: {
          50: '#EEF2FF',
          100: '#E0E7FF',
          500: '#6366F1',
          600: '#4F46E5',
          700: '#4338CA',
        },
      },
      boxShadow: {
        'soft-card': '0 10px 30px -5px rgba(15, 23, 42, 0.05), 0 4px 10px -2px rgba(15, 23, 42, 0.03)',
        'soft-hover': '0 20px 40px -10px rgba(15, 23, 42, 0.08)',
        'btn-glow': '0 8px 20px -4px rgba(99, 102, 241, 0.35)',
      },
      borderRadius: {
        'card': '20px',
        'tile': '14px',
      }
    }
  }
}
```

---

### Следующий шаг
Дизайн-система готова. Когда будете готовы, **предоставьте текст, который мы преобразуем в визуальное эссе**, и скажите, как вы хотите поступить:
1. Разбить текст на сцены/экраны по этой дизайн-системе.
2. Подготовить код верстки (HTML/Tailwind/компоненты).
3. Либо подключить приложенные навыки для генерации графических ассетов/схем.

## Review

Ваш первый драфт дизайн-системы — отличная база, но сейчас в нем есть **классическая ловушка «карго-культа»**: он описывает стандартный плоский SaaS-интерфейс на Tailwind, тогда как визуальная магия *Visual Clarity* держится на **7 микро-деталях верстки**, которые не видны при беглом просмотре. Если их упустить, получится просто «аккуратная веб-страница», а не клон референса.

Я провел попиксельный аудит кадров видео и ниже даю **Разбор расхождений (Anti-Cargo-Cult Audit)**, а затем — **Каноническую Дизайн-Систему v2.0** с точным кодом компонентов.

---

# ЧАСТЬ 1. Аудит: 7 главных отличий канона от вашего первого драфта

### 1. В референсе НЕТ плоских иконок — там тактильные «3D-кейкапы» (Keycap Tiles)
* **В вашем драфте:** Плоские квадраты `1px solid #E2E8F0` и плоские пастельные бейджи.
* **Как в видео на самом деле (кадры `00:24`, `00:47`, `01:15`, `02:09`):** Абсолютно каждый квадрат (и цветная иконка, и белая карточка технологии) имеет **тактильное 3D-дно (bottom lip)** толщиной `3px–4px` более темного оттенка и легкий вертикальный градиент сверху вниз. Они выглядят как физические кнопки клавиатуры. Без этой нижней кромки (`border-bottom: 3px solid ...`) стиль рассыпается.

### 2. Заголовки устроены совсем иначе (Два строгих типа)
* **В вашем драфте:** Сверху маленькая пилла `01 Reverse proxy`, под ней черный `H2`, под ним короткая полоска `40px`. **В видео нет ни одного такого кадра.**
* **Как в видео на самом деле:**
  * **Тип А (Концептуальный заголовок — кадры `00:01`, `00:16`, `00:26`, `01:01`):** Одна строка текста. Первая часть — почти черная (`#18181B`), а ключевые 1–2 слова — **ярко-фиолетовые (`#6D28D9`)**. Например: `An overwhelming list of` (черный) `technologies` (фиолетовый). Фиолетовая линия внизу (`height: 3.5px`, `width: ~72px`) лежит строго под началом первого слова.
  * **Тип Б (Номерная глава — кадры `01:09`, `01:37`, `02:48`, `03:37`):** Цифра `01` стоит **в одну строку слева** от текста внутри скругленного фиолетового квадрата (`28x28px`, `border-radius: 7px`), а сам текст заголовка (`Reverse proxy`) написан **целиком фиолетовым цветом**! Линия подчеркивания начинается от левого края квадратика `01`.

### 3. Два разных класса квадратных узлов (Role Tile vs Brand Tile)
В видео жестко разделены **Роли (абстрактные узлы)** и **Конкретные технологии (бренды)** (см. кадр `01:14` или `11:42`):
* **Role Tile (Роль: Proxy, Backend, Auth, DB, Cache, Queue):** Залита плотным сочным градиентом (зеленый, фиолетовый, малиновый, изумрудный, оранжевый) + внутри белая контурная иконка (`stroke-width: 2px`) + темное 3D-дно.
* **Brand Tile (Технология: NGINX, Stripe, Redis, Docker):** Чисто белая карточка (`#FFFFFF`), тонкая серая обводка `1.5px solid #E5E7EB`, серое 3D-дно `3px solid #D1D5DB` и цветной логотип внутри.

### 4. Фирменные угловые мини-бейджи (Corner Callout Badges)
Посмотрите на кадры `01:39` (`?`), `02:55` (`🔒`), `03:38` (`?`), `04:09` (`⚠️`), `05:18` (`⚡`), `08:53` (`📍`). Когда на узле возникает вопрос, ошибка, замок или свойство, в **правом верхнем углу** иконки (с нахлестом `-top-2 -right-2`) выскакивает круглый или квадратный мини-бейдж (`24x24px`) с белой обводкой `2px solid #FFFFFF`.

### 5. Специфическая верстка рамок-контейнеров (Кадры `04:44`, `06:08`, `07:32`)
Когда несколько элементов оборачиваются в контейнер (как `CACHE` на `04:44` или `CONTAINER` на `07:32` — и как будет выглядеть наша **`INTEGRATION`**):
* У контейнера **полупрозрачный пастельный фон** в цвет категории (например, `#FFF7ED` для оранжевого или `#F0FDFA` for бирюзового).
* **Акцентная полоса** (слева `border-left: 4px solid` как в `04:44` или сверху `height: 12px` как в `07:32`).
* Внутри контейнера в верхних углах лежат микро-бейджи: слева иконка + название (`CACHE`), справа — статус в пилле (`TEMPORARY`).

### 6. Подписи в схемах — строго `UPPERCASE` с широким трекингом
Внутри самих диаграмм (кадры `00:32`, `01:15`, `01:44`, `03:08`) нет обычного текста. Все метки (`USERS`, `REVERSE PROXY`, `BACKEND`, `VERIFIED`, `TEMPORARY`) набраны капсом (`11px–12px`, `font-weight: 700`, `letter-spacing: 0.08em`).

### 7. Переход между сценами — «Листание карточного слайда» (Page Push)
Посмотрите на секунды `00:15`, `01:00`, `02:59`, `05:32`. Сцены не просто меняются склейкой — новый белый холст **выезжает справа налево поверх старого** с мягкой вертикальной тенью на границе листа!

---

# ЧАСТЬ 2. Каноническая Дизайн-Система v2.0 (Pixel-Perfect клон референса)

## 1. Цветовая система и 3D-градиенты узлов (Canonical Color Tokens)

### 1.1. Холст и базовые поверхности
* `canvas-bg`: `#FFFFFF` (В видео фон — **чистый белый**, за счет чего пастельные контейнеры и тени карточек выглядят максимально контрастно).
* `card-surface`: `#FFFFFF`
* `card-border`: `#E5E7EB` (`1.5px solid`)
* `card-3d-lip`: `#D1D5DB` (нижний 3D-бортик белых карточек `border-bottom: 3px solid`)
* `dark-surface`: `#0F172A` (темные карточки на `01:50` и шапка логов на `04:11`)

### 1.2. Каноническая палитра ролей (с градиентами и 3D-дном)
Каждая сущность в вашей серии роликов должна использовать эти точные тройки (`Gradient` + `3D Lip` + `Tint BG`):

| Роль в системе | В Выпуске №1 (наша тема) | Основной градиент (Top → Bottom) | 3D-дно (`border-bottom: 3px`) | Пастельный фон контейнера |
| :--- | :--- | :--- | :--- | :--- |
| **Primary / Backend / API** | **API / CRM / Запрос** | `#7C3AED` → `#5B21B6` (Фиолетовый) | `#4C1D95` | `#F5F3FF` (рамка `#DDD6FE`) |
| **Event / Cache / Push** | **Webhook (Событие)** | `#F97316` → `#EA580C` (Оранжевый) | `#C2410C` | `#FFF7ED` (рамка `#FED7AA`) |
| **Database / Success / Paid** | **Payment (Paid) / Storage** | `#10B981` → `#059669` (Изумрудный) | `#047857` | `#ECFDF5` (рамка `#A7F3D0`) |
| **Auth / Security / Identity** | **Модуль Auth (Проверка)** | `#EC4899` → `#BE185D` (Малиновый) | `#9D174D` | `#FDF2F8` (рамка `#FBCFE8`) |
| **Queue / Mapping / Async** | **Модуль Mapping / Retry** | `#F59E0B` → `#D97706` (Янтарный) | `#B45309` | `#FFFBEB` (рамка `#FDE68A`) |
| **Container / Integration** | **Рамка INTEGRATION** | `#06B6D4` → `#0284C7` (Циан-Синий) | `#0369A1` | `#F0FDFA` (рамка `#99F6E4`) |
| **Danger / Alert / Load** | **Перегрузка / Ошибка** | `#EF4444` → `#DC2626` (Красный) | `#991B1B` | `#FEF2F2` (рамка `#FECACA`) |
| **Neutral / Actor / User** | **Покупатель / Неактивный** | `#475569` → `#334155` (Темно-серый) | `#1E293B` | `#F8FAFC` (рамка `#E2E8F0`) |

---

## 2. Типографика и правила регистра

1. **Гарнитура заголовков и UI:** `Plus Jakarta Sans` или `Inter` (начертания `600 SemiBold`, `700 Bold`, `800 ExtraBold`).
2. **Гарнитура кода и эндпоинтов:** `JetBrains Mono` (`500 Medium`, `600 SemiBold`).
3. **3 железных правила текста на экране:**
   * **На экране НЕТ абзацев текста.** Весь нарратив идет голосом. На экране — максимум 1–4 слова в плашке.
   * **Заголовки в углу (`H1`):** `28px–32px`, `font-weight: 700`, `letter-spacing: -0.02em`, строго в одну строку, без точки в конце.
   * **Подписи под узлами (`USERS`, `PAYMENT`, `SALES CRM`):** `12px`, `font-weight: 800`, `UPPERCASE`, `letter-spacing: 0.08em`, цвет `#1E293B`.

---

## 3. Эталонные компоненты (HTML / Tailwind CSS v2.0)

Ниже — готовая верстка ключевых узлов, снятая 1-в-1 с кадров референса.

### 3.1. Два канонических заголовка экрана (Header System)

```html
<!-- ТИП А: Концептуальный заголовок с фиолетовым акцентом (как на 00:01, 00:26, 01:01) -->
<div class="inline-block">
  <h1 class="text-[30px] font-bold tracking-tight text-zinc-900">
    One click, <span class="text-[#6D28D9]">an entire ecosystem</span>
  </h1>
  <!-- Линия строго под первым словом -->
  <div class="w-[76px] h-[3.5px] bg-[#6D28D9] rounded-full mt-2.5"></div>
</div>

<!-- ТИП Б: Номерная глава (как на 01:09 "01 Reverse proxy", 02:48 "03 Authentication") -->
<div class="inline-block">
  <div class="flex items-center gap-2.5">
    <span class="flex items-center justify-center w-7 h-7 rounded-[7px] bg-[#6D28D9] text-white text-sm font-extrabold">
      01
    </span>
    <h1 class="text-[30px] font-bold tracking-tight text-[#6D28D9]">
      API (Polling)
    </h1>
  </div>
  <!-- Линия начинается от левого края бейджа 01 -->
  <div class="w-[88px] h-[3.5px] bg-[#6D28D9] rounded-full mt-2.5"></div>
</div>
```

### 3.2. Тактильные 3D-узлы (Role Keycap Tile + Brand Tile + Угловой бейдж)

```html
<div class="flex items-center gap-12">

  <!-- 1. ROLE TILE: Цветной узел роли с 3D-дном и угловым бейджем вопроса (как на 01:39) -->
  <div class="flex flex-col items-center gap-2.5">
    <div class="relative flex items-center justify-center w-16 h-16 rounded-2xl bg-gradient-to-b from-[#7C3AED] to-[#5B21B6] border-b-[4px] border-[#4C1D95] shadow-[0_8px_20px_-4px_rgba(109,40,217,0.35)]">
      <!-- Белая контурная SVG-иконка (2px stroke) -->
      <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" d="M5 12h14M5 12a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v4a2 2 0 01-2 2M5 12a2 2 0 00-2 2v4a2 2 0 002 2h14a2 2 0 002-2v-4a2 2 0 00-2-2" />
      </svg>
      <!-- Угловой мини-бейдж (Corner Callout: ?, ⚠️, 🔒) -->
      <span class="absolute -top-2 -right-2 flex items-center justify-center w-6 h-6 rounded-full bg-[#EF4444] text-white text-xs font-extrabold ring-2 ring-white shadow-sm">
        !
      </span>
    </div>
    <span class="text-[11px] font-extrabold tracking-[0.08em] text-slate-800 uppercase">
      Sales CRM
    </span>
  </div>

  <!-- 2. BRAND TILE: Белая карточка конкретной технологии с 3D-дном (как на 00:08, 01:13) -->
  <div class="flex flex-col items-center gap-2.5">
    <div class="flex items-center justify-center w-16 h-16 rounded-2xl bg-white border-[1.5px] border-slate-200 border-b-[4px] border-b-slate-300 shadow-[0_8px_20px_-6px_rgba(15,23,42,0.08)]">
      <!-- Сюда вставляется официальный SVG логотипа (Stripe, Redis, Webhook) -->
      <span class="text-xl font-black text-[#635BFF]">S</span>
    </div>
    <span class="text-[12px] font-bold text-slate-700">
      Stripe
    </span>
  </div>

</div>
```

### 3.3. Каноническое окно логов `requests.log` (Клон кадра `04:11` для Сцены 2)
Обратите внимание, как именно в референсе сделан спам запросов на `04:11`: темная шапка со светофором, белое тело окна, серые плашки обычных запросов и **желто-янтарная подсветка повторяющихся запросов** с иконкой повтора справа.

```html
<!-- Окно requests.log (Клон 04:11) -->
<div class="w-[540px] rounded-2xl bg-white border-[1.5px] border-slate-200 border-b-[4px] border-b-slate-300 shadow-[0_20px_40px_-15px_rgba(15,23,42,0.1)] overflow-hidden">
  <!-- Темная шапка окна -->
  <div class="flex items-center justify-between px-4 py-2.5 bg-[#0F172A]">
    <div class="flex items-center gap-1.5">
      <span class="w-2.5 h-2.5 rounded-full bg-[#EF4444]"></span>
      <span class="w-2.5 h-2.5 rounded-full bg-[#F59E0B]"></span>
      <span class="w-2.5 h-2.5 rounded-full bg-[#10B981]"></span>
    </div>
    <span class="font-mono text-xs font-medium text-slate-300">requests.log</span>
    <span class="flex items-center gap-1 px-2 py-0.5 rounded bg-slate-800 text-[10px] font-bold text-emerald-400 tracking-wider">
      <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 animate-pulse"></span> LIVE
    </span>
  </div>

  <!-- Список запросов -->
  <div class="p-3 space-y-2 bg-white font-mono text-xs">
    <!-- Повторяющийся запрос (Подсвечен желтым, как на 04:20) -->
    <div class="flex items-center justify-between px-3 py-2 rounded-lg bg-[#FEF9C3] border border-[#FDE047] text-slate-800">
      <div class="flex items-center gap-2.5">
        <span class="w-5 h-5 rounded-full bg-[#6D28D9] text-white flex items-center justify-center text-[10px] font-bold">C</span>
        <span class="font-bold text-amber-800">GET</span>
        <span class="font-semibold">/orders/1042/status</span>
      </div>
      <span class="text-xs font-bold text-amber-700">200 Unpaid ↻</span>
    </div>

    <!-- Обычная строка лога -->
    <div class="flex items-center justify-between px-3 py-2 rounded-lg bg-slate-50 text-slate-500">
      <div class="flex items-center gap-2.5">
        <span class="w-5 h-5 rounded-full bg-slate-400 text-white flex items-center justify-center text-[10px] font-bold">C</span>
        <span class="font-bold text-slate-400">GET</span>
        <span>/orders/1042/status</span>
      </div>
      <span class="text-[11px]">200 Unpaid</span>
    </div>
  </div>
</div>
```

### 3.4. Каноническая рамка-контейнер (Клон `04:44` Cache и `07:32` Docker для Сцены 5 «INTEGRATION»)
Именно так в референсе упаковываются внутренние процессы в единую сущность:

```html
<!-- Контейнер INTEGRATION (по канону 04:44 и 07:32) -->
<div class="relative w-[560px] rounded-2xl bg-[#F0FDFA] border-[1.5px] border-[#5EEAD4] border-t-[10px] border-t-[#0D9488] p-6 shadow-sm">
  <!-- Верхняя строка мета-информации контейнера -->
  <div class="flex items-center justify-between mb-5">
    <div class="flex items-center gap-2">
      <span class="w-5 h-5 rounded bg-[#0D9488] text-white flex items-center justify-center text-xs font-bold">⚙</span>
      <span class="text-xs font-extrabold tracking-[0.08em] text-[#0F766E] uppercase">Integration Layer</span>
    </div>
    <span class="px-2.5 py-0.5 rounded-full bg-[#CCFBF1] text-[#0F766E] text-[10px] font-extrabold tracking-wider uppercase">
      Automated
    </span>
  </div>

  <!-- 4 внутренних модуля (как 4 иконки внутри Docker на 07:31) -->
  <div class="grid grid-cols-4 gap-4">
    <div class="flex flex-col items-center gap-2 p-3 rounded-xl bg-white/80 border border-teal-100">
      <div class="w-11 h-11 rounded-xl bg-gradient-to-b from-[#EC4899] to-[#BE185D] border-b-[3px] border-[#9D174D] flex items-center justify-center text-white font-bold">🔑</div>
      <span class="text-[10px] font-extrabold tracking-wider text-slate-700 uppercase">Auth</span>
    </div>
    <div class="flex flex-col items-center gap-2 p-3 rounded-xl bg-white/80 border border-teal-100">
      <div class="w-11 h-11 rounded-xl bg-gradient-to-b from-[#F59E0B] to-[#D97706] border-b-[3px] border-[#B45309] flex items-center justify-center text-white font-bold">🔄</div>
      <span class="text-[10px] font-extrabold tracking-wider text-slate-700 uppercase">Mapping</span>
    </div>
    <div class="flex flex-col items-center gap-2 p-3 rounded-xl bg-white/80 border border-teal-100">
      <div class="w-11 h-11 rounded-xl bg-gradient-to-b from-[#10B981] to-[#059669] border-b-[3px] border-[#047857] flex items-center justify-center text-white font-bold">🔁</div>
      <span class="text-[10px] font-extrabold tracking-wider text-slate-700 uppercase">Retries</span>
    </div>
    <div class="flex flex-col items-center gap-2 p-3 rounded-xl bg-white/80 border border-teal-100">
      <div class="w-11 h-11 rounded-xl bg-gradient-to-b from-[#3B82F6] to-[#2563EB] border-b-[3px] border-[#1D4ED8] flex items-center justify-center text-white font-bold">📊</div>
      <span class="text-[10px] font-extrabold tracking-wider text-slate-700 uppercase">Logs</span>
    </div>
  </div>
</div>
```

### 3.5. Темная рентген-панель «Behind the scenes» (Клон кадра `01:50`)
В референсе, когда нужно показать внутренние шаги системы (на `01:50`), появляется контрастный темно-синий блок (`#0B1120`) с пронумерованными карточками внутри (`01`, `02`, `03`, `04`), которые по очереди обводятся цветной рамкой по ходу голоса диктора.

* **Фон блока:** `#0B1120`, `border-radius: 20px`, `padding: 24px`.
* **Внутренние мини-карточки:** фон `#131C31`, `border-radius: 14px`, в левом верхнем углу мелкая цифра `01` (`#475569`).
* **Активная внутренняя карточка:** получает яркую цветную рамку `1.5px solid #F59E0B` (или `#6D28D9`), а остальные карточки остаются приглушенными (`opacity: 0.45`).

---

## 4. Система анимации и хореографии (Motion Tokens)

Чтобы картинка двигалась как в референсе, зафиксируйте 4 анимационных закона:

1. **Пружинный скейл появления иконок (Pop-in):**
   * Узлы никогда не появляются просто через `opacity`. Они вырастают из `scale(0.85)` до `scale(1)` с легким перелетом (`cubic-bezier(0.34, 1.56, 0.64, 1)`, длительность `280ms`).
2. **Рисование линий и движение пакетов (Line Draw & Packet Travel):**
   * Сначала от узла А к узлу Б рисуется серая базовая линия (`#CBD5E1`, `2px`).
   * В момент запроса поверх нее пробегает цветной луч или едет бейдж-конвертик (`duration: 450ms`, `cubic-bezier(0.4, 0, 0.2, 1)`).
   * Когда пакет долетает до узла Б, узел Б делает микро-пульс: `scale(1) → scale(1.06) → scale(1)` за `200ms`.
3. **Закон фокуса (Dimming Inactive Nodes):**
   * Когда на экране 4 элемента, а диктор говорит только про второй — у элементов `1, 3, 4` прозрачность падает до `opacity: 0.25` (как на `01:53` или `11:39`). Взгляд зрителя всегда прикован только к одной точке.
4. **Фирменный переход между главами (Page Push Wipe — кадры `00:15`, `01:00`, `02:59`):**
   * Новый экран выезжает справа (`translateX(100%) → translateX(0%)` за `500ms`, `cubic-bezier(0.22, 1, 0.36, 1)`), отбрасывая мягкую тень `-20px 0 40px rgba(0,0,0,0.07)` на уходящий влево старый экран (`translateX(0%) → translateX(-18%)`).

---

### Как применить это прямо сейчас для Выпуска №1:
Теперь у вас есть **абсолютно точный визуальный геном**:
1. Белый холст `#FFFFFF`.
2. Заголовки двух канонических типов (с фиолетовым акцентом и инлайн-квадратиком `01`).
3. Тактильные 3D-плитки с нижним бортиком `border-bottom: 3px/4px`.
4. Окно `requests.log` с желтыми строками повторов для демонстрации проблемы Polling в API.
5. Пастельный контейнер с цветной крышкой для упаковки `INTEGRATION`.


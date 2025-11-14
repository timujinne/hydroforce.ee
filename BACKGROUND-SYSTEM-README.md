# Система фоновых изображений - Hydroforce

## Обзор

В `hydroforce-styles.css` интегрирована система фоновых изображений с использованием CSS custom properties. Все стили градиентов, позиционирования и размеров централизованы в CSS файле — в HTML передается только URL изображения.

## Преимущества

✅ **Чистый HTML** - только URL изображения в инлайн-стиле
✅ **Централизованные стили** - все градиенты и эффекты в CSS
✅ **Легкая поддержка** - изменения в одном месте
✅ **Автоматическая оптимизация** - `fixed` → `scroll` на мобильных
✅ **Лучшая производительность** - оптимизация браузера для CSS custom properties

## Доступные классы

### 1. `.hero-bg` - Стандартный темный градиент

**Использование:**
```html
<section class="hero-bg" style="--bg-image: url('path/to/image.jpg');">
    <div class="container">
        <h1>Заголовок</h1>
        <p>Текст</p>
    </div>
</section>
```

**Характеристики:**
- Градиент: темный сверху → прозрачный снизу
- Цвет текста: белый
- Text shadow: да
- Лучше всего для: hero-секций, основных баннеров

---

### 2. `.hero-bg-dark` - Очень темный оверлей

**Использование:**
```html
<section class="hero-bg-dark" style="--bg-image: url('path/to/image.jpg');">
    <!-- Контент -->
</section>
```

**Характеристики:**
- Градиент: очень темный (85% непрозрачность)
- Цвет текста: белый
- Лучше всего для: секций с максимальной читаемостью текста

---

### 3. `.hero-bg-light` - Светлый оверлей

**Использование:**
```html
<section class="hero-bg-light" style="--bg-image: url('path/to/image.jpg');">
    <!-- Контент -->
</section>
```

**Характеристики:**
- Градиент: светлый (белый/светло-серый с 85% непрозрачностью)
- Цвет текста: темный (var(--text-gray))
- Заголовки: синие (var(--primary-blue))
- Лучше всего для: контентных секций с темным текстом

---

### 4. `.hero-bg-gradient-lr` - Градиент слева направо

**Использование:**
```html
<section class="hero-bg-gradient-lr" style="--bg-image: url('path/to/image.jpg');">
    <!-- Контент -->
</section>
```

**Характеристики:**
- Градиент: слева темный → справа прозрачный
- Лучше всего для: асимметричных макетов с текстом слева

---

### 5. `.hero-bg-gradient-rl` - Градиент справа налево

**Использование:**
```html
<section class="hero-bg-gradient-rl" style="--bg-image: url('path/to/image.jpg');">
    <!-- Контент -->
</section>
```

**Характеристики:**
- Градиент: справа темный → слева прозрачный
- Лучше всего для: асимметричных макетов с текстом справа

---

### 6. `.cta-bg` - CTA секция с фоном

**Использование:**
```html
<section class="cta-bg" style="--bg-image: url('path/to/image.jpg');">
    <div class="container">
        <h2>Готовы начать?</h2>
        <p>Свяжитесь с нами сегодня</p>
        <a href="#" class="btn btn-cta">Связаться</a>
    </div>
</section>
```

**Характеристики:**
- Градиент: красный (accent-red) с 90% непрозрачностью
- Цвет текста: белый
- Лучше всего для: call-to-action секций

---

## Миграция со старого синтаксиса

### Было:
```html
<section class="hero-overlay" style="
    background: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.5)),
    url('image.jpg');
    background-size: cover;
    background-position: center;">
```

### Стало:
```html
<section class="hero-bg" style="--bg-image: url('image.jpg');">
```

---

## Автоматическая оптимизация

На мобильных устройствах (`max-width: 768px`) все секции автоматически переключаются с `background-attachment: fixed` на `scroll` для улучшения производительности.

---

## Дополнительные улучшения в hydroforce-styles.css

### 1. Fluid Typography
Автоматическое масштабирование шрифтов с помощью `clamp()`:
```css
h1 { font-size: clamp(2rem, 5vw + 1rem, 3rem); }
h2 { font-size: clamp(1.75rem, 4vw + 0.5rem, 2.5rem); }
```

### 2. Accessibility (Доступность)
- Focus states для кнопок и ссылок
- Поддержка `prefers-reduced-motion`
- Правильные ARIA roles и labels

### 3. Spacing Scale
Унифицированная шкала отступов:
```css
--space-xs: 0.5rem;
--space-sm: 1rem;
--space-md: 1.5rem;
--space-lg: 2rem;
--space-xl: 3rem;
--space-2xl: 4rem;
```

---

## Примеры использования

### Hero секция (стандартная):
```html
<section class="hero-bg" style="--bg-image: url('https://example.com/hero.jpg');">
    <div class="container">
        <h1>Hydraulic Motors and Pumps</h1>
        <p class="hero-subtitle">Engineered for reliable performance</p>
        <div class="hero-stats">
            <span><strong>25+</strong> Years of Expertise</span>
            <span><strong>500+</strong> Motor Models</span>
        </div>
        <div class="hero-buttons">
            <a href="#" class="btn btn-primary">Get Started</a>
            <a href="#" class="btn btn-secondary">Learn More</a>
        </div>
    </div>
</section>
```

### Контентная секция со светлым фоном:
```html
<section class="hero-bg-light" style="--bg-image: url('https://example.com/bg.jpg');">
    <div class="container">
        <div class="section-header">
            <h2>Our Advantages</h2>
            <p>Cost-effective precision manufacturing</p>
        </div>
        <div class="grid-3">
            <div class="card">
                <h3>Quality</h3>
                <p>ISO certified production</p>
            </div>
            <!-- Больше карточек -->
        </div>
    </div>
</section>
```

### CTA секция:
```html
<section class="cta-bg" style="--bg-image: url('https://example.com/cta-bg.jpg');">
    <div class="container">
        <h2>Ready to Get Started?</h2>
        <p>Contact us today for a consultation</p>
        <a href="#contact" class="btn btn-cta">Contact Us</a>
    </div>
</section>
```

---

## Поддержка браузеров

✅ Chrome 49+
✅ Firefox 31+
✅ Safari 9.1+
✅ Edge 15+
✅ Opera 36+

CSS custom properties поддерживаются всеми современными браузерами.

---

## Troubleshooting

### Изображение не отображается
- Проверьте правильность URL
- Убедитесь, что используется `url('...')` синтаксис
- Проверьте CORS настройки для внешних изображений

### Текст плохо читается
- Используйте `.hero-bg-dark` для темного оверлея
- Используйте `.hero-bg-light` для светлого оверлея
- Настройте непрозрачность в CSS при необходимости

### На мобильных устройствах фон дергается
Это нормально - `background-attachment: fixed` автоматически переключается на `scroll` на мобильных для лучшей производительности.

---

## Контакты и поддержка

Для вопросов и предложений обращайтесь к документации проекта или в репозиторий GitHub.

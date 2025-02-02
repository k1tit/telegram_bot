# telegram_bot
***
Telegram-бот, предназначенный для поиска информации о пищевой ценности продуктов (КБЖУ: калории, белки, жиры, углеводы). Бот использует API сервиса FatSecret для получения данных о продуктах питания и поддерживает возможность поиска как на русском, так и на английском языке.

 Основной функционал:

 1. Получение данных о пищевой ценности продуктов:
Пользователь может ввести название любого продукта (например, "яблоко" или "куриная грудка"), и бот ответит информацией о его пищевой ценности: количество калорий, белков, жиров и углеводов.
Для удобства бот переводит русскоязычные названия продуктов на английский с помощью Google Translate, так как база данных FatSecret преимущественно работает на английском языке.

 2. Интеграция с API FatSecret:
Для получения информации о продуктах бот использует FatSecret API. Он выполняет OAuth-аутентификацию для получения токена доступа, который позволяет ему делать запросы к сервису.

 3. Асинхронная обработка запросов:
Все запросы к API, переводы текста и ответы бота происходят асинхронно, что делает работу бота более быстрой и отзывчивой. Бот использует библиотеку aiohttp для асинхронных HTTP-запросов и aiogram для управления событиями и взаимодействия с Telegram.

 4. Удобный интерфейс с клавиатурой:
Бот предлагает встроенные клавиатуры для взаимодействия с пользователем. Например, при нажатии кнопки "Узнать КБЖУ" пользователь может быстро запросить данные о продукте.

 5. Многоязычная поддержка:
Основной язык работы с API — английский, однако бот поддерживает русскоязычные запросы благодаря встроенному переводчику Google Translate. Если пользователь вводит название продукта на русском языке, бот переведет его на английский и отправит запрос в FatSecret.
 
 **Как бот работает:**
1. Пользователь отправляет команду /start, после чего бот приветствует пользователя и предлагает ввести название продукта для поиска КБЖУ.
2. Когда пользователь вводит название продукта (например, "Куриная грудка"), бот:
  * Переводит название на английский с помощью googletrans.
  * Получает доступ к API FatSecret, выполняя OAuth-аутентификацию для получения access-токена.
  * Выполняет запрос к API для поиска продукта по его английскому названию.
  * Обрабатывает ответ от API, извлекая данные о калориях, белках, жирах и углеводах.
  * Отправляет пользователю сообщение с результатами.
3. Если продукт не найден или произошла ошибка, бот уведомит об этом пользователя.
 **Технические детали:**
* Язык разработки: Python
* Библиотеки:
  * **aiogram** — для создания бота и управления событиями Telegram.
  * **aiohttp** — для выполнения асинхронных HTTP-запросов.
  * **googletrans** — для перевода названий продуктов с русского на английский.
  * **python-dotenv** — для загрузки переменных окружения (ключей API).
  * **FatSecret API** — для получения информации о пищевой ценности продуктов.

# Финансовый ассистент на базе GigaChat и LangGraph

Этот проект представляет собой финансового ассистента, разработанного с использованием моделей GigaChat и библиотек LangChain и LangGraph. Ассистент способен управлять банковскими счетами и картами пользователя, предоставляя информацию о балансе, истории транзакций, а также выполняя переводы и блокировку карт.

## Описание

Ассистент реализован на Python и использует следующие библиотеки:

- **langchain**: Фреймворк для создания приложений на основе больших языковых моделей (LLM). Предоставляет стандартный интерфейс для взаимодействия с моделями и другими компонентами, что упрощает разработку линейных цепочек вызовов и интеграцию различных сервисов.  
  *Amazon Web Services, Inc.*

- **langchain_gigachat**: Интеграция GigaChat с LangChain, позволяющая использовать возможности GigaChat в приложениях на основе LangChain.

- **langchain_community**: Набор интеграций и инструментов для LangChain, включая адаптеры для различных сервисов и API.

- **langgraph**: Библиотека для создания и управления графами в контексте языковых моделей. В отличие от LangChain, LangGraph позволяет строить сложные, нелинейные цепочки вызовов и зависимости, что особенно полезно для разработки мультиагентных систем с разветвлённой логикой.

Код был разработан и протестирован в среде Google Colab, что позволяет легко воспроизвести результаты и адаптировать проект под собственные нужды.

## Начало работы

### Установка зависимостей

Перед запуском необходимо установить все требуемые библиотеки. В Google Colab это можно сделать с помощью следующей команды:

```
!pip install -q langchain langchain_gigachat langchain_community langgraph
```



### Настройка доступа к GigaChat

Для работы с GigaChat требуется авторизация. В данном проекте используется токен доступа, сохранённый в переменной окружения `GIGA_TOKEN` в Google Colab. Это позволяет не раскрывать токен в коде.

#### Получение токена доступа

Чтобы получить токен доступа к GigaChat API:

1. **Регистрация в личном кабинете**: Перейдите на страницу регистрации и создайте аккаунт, если у вас его нет.
2. **Создание проекта**: После входа в личный кабинет создайте новый проект, выбрав GigaChat API.
3. **Получение ключа авторизации**: В настройках проекта сгенерируйте новый ключ авторизации (Authorization Key). Сохраните его в надёжном месте, так как он отображается только один раз.
4. **Сохранение токена в Google Colab**: Выполните следующую команду в ячейке Colab, заменив `'your_authorization_key'` на ваш ключ:

```
from google.colab import userdata
userdata.set('GIGA_TOKEN', 'your_authorization_key')
```

Теперь токен будет доступен в коде через `userdata.get('GIGA_TOKEN')`.

#### Альтернативные способы авторизации

Помимо использования токена, GigaChat поддерживает другие методы авторизации:

- **Логин и пароль**: Можно использовать учётные данные для доступа к сервису.
- **Сертификаты TLS**: Авторизация с использованием клиентских сертификатов.
- **Access Token**: Получение токена доступа через запрос к API.

Подробнее о способах авторизации можно узнать в официальной документации.

## Использование

После настройки окружения и авторизации вы можете запустить код ассистента. В интерактивном режиме ассистент будет обрабатывать ваши запросы, такие как:

- **Просмотр баланса**: "Каков мой текущий баланс?"
- **История транзакций**: "Покажи историю моих транзакций."
- **Список привязанных карт**: "Какие карты привязаны к моему счету?"
- **Перевод средств**: "Переведи 2000 рублей Петрову Ивану."
- **Блокировка карты**: "Заблокируй мою карту с номером 2202208XXXX11824 по причине утери."

Эти примеры демонстрируют основные возможности ассистента по управлению банковскими счетами и картами.

## Примечания

- **Безопасность токена**: Рекомендуется не хранить токен непосредственно в коде. Использование переменных окружения или других методов хранения повышает безопасность.
- **Дополнительная информация**: Для более детального ознакомления с GigaChat API и его возможностями посетите официальную документацию.

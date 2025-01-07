# Sequence

### Оформление и оплата услуг

![Sequence](/material/Sequence.png)

<details>
  <summary>Код Sequence diagram</summary>
  
```plaintext

@startuml
actor Client
participant "Mobile/Web App" as App
participant "API" as API
participant "База данных" as DB
participant "Платежная система" as PaymentSystem

Client -> App: Нажимает кнопку "Оплатить"
App -> App: Проверка выбранных пунктов (Автомойка, услуги, машина, дата, время)
alt Все пункты выбраны
    App -> API: Запрос на создание заказа
    API -> DB: Создание записи о заказе
    DB --> API: ID заказа
    API -> PaymentSystem: Запрос на создание платежной формы
    PaymentSystem --> API: Данные для платежной формы (URL, параметры)
    API --> App: ID заказа и ID оплаты
    WebApp --> Client: Отображение данных заказа и переход к платежной форме
    
    Client -> PaymentSystem: Вводит данные карты (через страницу платежной системы)
    
    PaymentSystem -> PaymentSystem: Проверка платежа
    alt Успешная оплата
        PaymentSystem --> API: Успешная оплата
        API -> DB: Обновление статуса заказа на "Оплачено"
        DB --> API: Подтверждение обновления
        API --> App: Подтверждение оплаты
        App --> Client: Отображение подтверждения оплаты и ID заказа
    else Неуспешная оплата
        PaymentSystem --> API: Ошибка оплаты
        API --> App: Ошибка оплаты
        App --> Client: Отображение сообщения об ошибке
    end
else  Не все пункты выбраны
    App --> Client: Сообщение об ошибке
end
@enduml

```

</details>


# PRACT_API

# Основные сущности

# Таблица Car
| Поле           | Тип данных     | Описание                                        |
| -------------- | -------------- | ----------------------------------------------- |
| `id`           | `Integer` (PK) | Уникальный идентификатор автомобиля             |
| `model`        | `String`       | Название модели, например: "Toyota Corolla"     |
| `engine`       | `String`       | Тип двигателя, например: "ДВС"                  |
| `color`        | `String`       | Цвет автомобиля, например: "Синий"              |
| `price`        | `Float`        | Цена автомобиля в денежном выражении            |
| `body_style`   | `String`       | Тип кузова: "Sedan", "Hatchback", "SUV" и т.д.  |
| `transmission` | `String`       | Тип трансмиссии: "Автомат", "Механика" и т.д.   |
| `dealer_id`    | `Integer`      | ID дилера, у которого находится автомобиль (FK) |

# Таблица Customer
| Поле            | Тип данных     | Описание                                                  |
| --------------- | -------------- | --------------------------------------------------------- |
| `id`            | `Integer` (PK) | Уникальный идентификатор покупателя                       |
| `phone_number`  | `String`       | Телефонный номер покупателя, например: "+7-999-123-45-67" |
| `name`          | `String`       | Имя покупателя                                            |
| `gender`        | `String`       | Пол: "Мужской", "Женский" и т.д.                          |
| `annual_income` | `Float`        | Годовой доход покупателя                                  |
| `car_id`        | `Integer`      | ID автомобиля, который купил данный клиент (FK)           |

# Таблица Dealer
| Поле          | Тип данных     | Описание                                         |
| ------------- | -------------- | ------------------------------------------------ |
| `id`          | `Integer` (PK) | Уникальный идентификатор дилера                  |
| `dealer_no`   | `String`       | Номер дилера, уникальный код, например: "DLR001" |
| `name`        | `String`       | Название дилерской компании                      |
| `region_name` | `String`       | Название региона, связанного с дилером (FK)      |

# Таблица Region
| Поле          | Тип данных    | Описание                                  |
| ------------- | ------------- | ----------------------------------------- |
| `region_name` | `String` (PK) | Название региона, например: "Центральный" |

# ER-Диаграмма
![image](https://github.com/user-attachments/assets/ba6c3060-3f13-49e1-bbfd-cd198a8b44ea)

# Диаграмма основных действий приложения
![image](https://github.com/user-attachments/assets/f6c4a527-2cad-4a7d-9ffa-50622f7d1fb9)

# Согласование магических строк
| Поле           | -> | Описание                                        |
| -------------- | -- | ----------------------------------------------- |
| `id`           | -> | identifier                                      |
| `model`        | -> | vehicleModel                                    |
| `engine`       | -> | vehicleEngine                                   |
| `color`        | -> | color                                           |
| `price`        | -> | price                                           |
| `body_style`   | -> | bodyType                                        |
| `transmission` | -> | vehicleTransmission                             |
| `dealer_id`    | -> | dealerIdentifier                                |
| `read-list`    | -> | collection                                      |
| `filter_list`  | -> | search                                          |
| `read-car`     | -> | item                                            |
| `create-car`   | -> | create-item                                     |
| `update-car`   | -> | edit                                            |
| `delete-car`   | -> | delete-item                                     |

# Диаграмма после согласования имен
![image](https://github.com/user-attachments/assets/6a234d70-6251-4315-885a-d5587af4636f)

# Создание семантического профиля
{
  "items": [
    {
      "id": 1,
      "model": "Toyota Corolla",
      "color": "Синий",
      "price": 19500.0,
      "body_style": "Sedan",
      "transmission": "Автомат",
      "dealer": {
        "id": 2,
        "dealer_no": "DLR002",
        "name": "Тойота Центр",
        "region": {
          "region_name": "Центральный"
        }
      }
    },
    ...
  ]
}

# Преобразование к hypermedia
{
  "_links": {
    "self": { "href": "/cars" }
  },
  "_embedded": {
    "cars": [
      {
        "id": 1,
        "model": "Toyota Corolla",
        "color": "Синий",
        "price": 19500.0,
        "body_style": "Sedan",
        "transmission": "Автомат",
        "_links": {
          "self": { "href": "/cars/1" },
          "dealer": { "href": "/dealers/2" }
        },
        "dealer": {
          "id": 2,
          "dealer_no": "DLR002",
          "name": "Тойота Центр",
          "_links": {
            "self": { "href": "/dealers/2" },
            "region": { "href": "/regions/Центральный" }
          },
          "region": {
            "region_name": "Центральный",
            "_links": {
              "self": { "href": "/regions/Центральный" }
            }
          }
        }
      }
    ]
  }
}

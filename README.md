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
![image](https://github.com/user-attachments/assets/68972a86-cb3f-429e-a226-bdf912a64569)


# Согласование магических строк
| Поле           | -> | Описание                                        |
| -------------- | -- | ----------------------------------------------- |
| `id`           | -> | identifier                                      |
| `model`        | -> | model                                           |
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
![image](https://github.com/user-attachments/assets/b0494229-ec44-4c56-b85e-abe97a4fde5f)



# Создание семантического профиля
![image](https://github.com/user-attachments/assets/057751ca-0570-4882-a6cb-e798e7973c14)


# Преобразование к hypermedia
![image](https://github.com/user-attachments/assets/3fbf044d-8de1-440c-bfec-d8cd156b337e)


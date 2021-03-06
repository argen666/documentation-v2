---
title: Инвентаризация
permalink: rest_inventory.html
sidebar: evorestreference
product: Customer API
---

### `INVENTORY`

```json
{
  "body": {
    "positions": [
      {
        "position": {
          "product_id": "1022722e-9441-4beb-beae-c6bc5e7af30d",
          "quantity": 123.123,
          "initial_quantity": 123.123,
          "code": "42",
          "id": 12,
          "uuid": "1022722e-9441-4beb-beae-c6bc5e7af30d",
          "extra_keys": [
            {
              "extra_key": {
                "identity": "string",
                "app_id": "string",
                "description": "string"
              }
            }
          ]
        }
      }
    ],
    "complete_inventory": true
  }
}
```

Имя  | Тип  | Описание
-----|------|--------------
`positions`|`Array of object`|Массив товарных позиций (объектов position).
`complete_inventory`|`boolean`|*Необязательный*. Определяет является инвентаризация полной или нет. `true` (значение по умолчанию) -- инвентаризация полная (остатки меняются у всех товаров; у неупомянутых товаров остаток сбрасывается к нулю). `false` - инвентаризация частичная (остатки меняются только у перечисленных позиций).
`positions.position`|`object`|Товарная позиция.
`positions.position.product_id`|`string`|Идентификатор товара, уникальный в рамках магазина. Поле не передаётся, если производится продажа или возврат товара "Позиция по свободной цене". Формат uuid4, в соответствии с RFC.
`positions.position.quantity`|`number`|Количество товара, над которыми выполняется операция. Всегда положительное и содержит до трёх знаков в дробной части.
`positions.position.initial_quantity`|`integer`|Остаток товара до выполнения операции. До трёх знаков в дробной части.
`positions.position.code`|`string`|Код товара или модификации товара. Поле не передаётся, если производится продажа или возврат товара "Позиция по свободной цене".
`positions.position.id`|`integer`|Порядковый номер транзакции регистрации позиции в документе. Счет ведется на уровне терминала, начиная с единицы. Номер можно сбросить программно.
`positions.position.uuid`|`string`|*Необязательный*. Уникальный идентификатор товарной позиции в чеке. Полезен в случаях, когда нужно программно (средствами SDK) сослаться на конкретную позицию.
`positions.position.extra_keys`|`Array of object`|*Необязательный*. Массив объектов `extra_key`, соответствующих extra товара, на момент добавления товара в документ.
`positions.position.extra_keys.extra_key`|`object`|*Необязательный*. Массив объектов `extra_key`, соответствующих extra товара, на момент добавления товара в документ.
`positions.position.extra_keys.extra_key.identity`|`string`|*Необязательный*. Уникальный идентификатор дополнительного атрибута товара. Формат – uuid4, в соответствии с RFC.
`positions.position.extra_keys.extra_key.app_id`|`string`|*Необязательный*. Идентификатор приложения, в рамках которого к товарной позиции привязан дополнительный атрибут.
`positions.position.extra_keys.extra_key.description`|`string`|*Необязательный*. Описание дополнительного атрибута для визуализации на смарт-терминале.

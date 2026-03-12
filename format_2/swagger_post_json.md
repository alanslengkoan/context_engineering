# POST - Create Resource (JSON)

## Overview
Endpoint untuk membuat resource baru dengan request body JSON.

## Endpoint
```
POST /{{endpoint}}
```

## Variables
- `{{endpoint}}` => nama endpoint
- `{{tag}}` => kategori tag Swagger
- `{{summary}}` => deskripsi singkat endpoint
- `{{properties}}` => daftar property sesuai kebutuhan
- `{{required_fields}}` => daftar field yang wajib diisi
- `{{example}}` => contoh data request

## Content-Type
```
application/json
```

---

## Template Swagger
```php
/**
 * @OA\Post(
 *      path="/{{endpoint}}",
 *      summary="{{summary}}",
 *      tags={"{{tag}}"},
 *      @OA\RequestBody(
 *          @OA\MediaType(
 *              mediaType="application/json",
 *              @OA\Schema(
 *                  {{properties}}
 *                  required={{required_fields}},
 *                  example={{example}}
 *              )
 *          )
 *      ),
 *      @OA\Response(
 *          response=201,
 *          description="Created successfully"
 *      ),
 *      @OA\Response(
 *          response=422,
 *          description="Validation error"
 *      ),
 *      @OA\Response(
 *          response=401,
 *          description="Unauthorized"
 *      ),
 *      security={{ "bearerAuth": {} }}
 * )
 */
```

---

## Property Template

### String Property
```php
@OA\Property(
    property="{{field_name}}",
    type="string",
    description="{{description}}"
),
```

### Integer Property
```php
@OA\Property(
    property="{{field_name}}",
    type="integer",
    description="{{description}}"
),
```

### Number (Double) Property
```php
@OA\Property(
    property="{{field_name}}",
    type="number",
    format="double",
    description="{{description}}"
),
```

### Date Property
```php
@OA\Property(
    property="{{field_name}}",
    type="string",
    format="date",
    description="{{description}}"
),
```

### Enum Property
```php
@OA\Property(
    property="{{field_name}}",
    type="string",
    enum={"value1", "value2", "value3"},
    description="{{description}}"
),
```

### Array Property
```php
@OA\Property(
    property="{{field_name}}",
    type="array",
    description="{{description}}",
    @OA\Items(
        type="string"
    )
),
```

---

## Example Usage
```php
/**
 * @OA\Post(
 *      path="/invoice-bills",
 *      summary="Create a new invoice bill",
 *      tags={"Finance - Invoice Bills"},
 *      @OA\RequestBody(
 *          @OA\MediaType(
 *              mediaType="application/json",
 *              @OA\Schema(
 *                  @OA\Property(
 *                      property="id_type_transaction",
 *                      type="integer",
 *                      description="Type Transaction ID"
 *                  ),
 *                  @OA\Property(
 *                      property="type",
 *                      type="string",
 *                      enum={"transaction", "transaction_full", "down_payment", "advance_payment"},
 *                      description="Type"
 *                  ),
 *                  @OA\Property(
 *                      property="date",
 *                      type="string",
 *                      format="date",
 *                      description="Date"
 *                  ),
 *                  @OA\Property(
 *                      property="total",
 *                      type="number",
 *                      format="double",
 *                      description="Total"
 *                  ),
 *                  @OA\Property(
 *                      property="description",
 *                      type="string",
 *                      description="Description"
 *                  ),
 *                  required={"id_type_transaction", "type", "date", "total"},
 *                  example={
 *                      "id_type_transaction": 1,
 *                      "type": "transaction",
 *                      "date": "2023-01-01",
 *                      "total": 100000,
 *                      "description": "Pembayaran"
 *                  }
 *              )
 *          )
 *      ),
 *      @OA\Response(
 *          response=201,
 *          description="Created successfully"
 *      ),
 *      @OA\Response(
 *          response=422,
 *          description="Validation error"
 *      ),
 *      @OA\Response(
 *          response=401,
 *          description="Unauthorized"
 *      ),
 *      security={{ "bearerAuth": {} }}
 * )
 */
```
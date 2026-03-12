# PUT - Update Resource (JSON)

## Overview
Endpoint untuk update resource menggunakan request body JSON.

## Endpoint
```
PUT /{{endpoint}}/{id}
```

## Variables
- `{{endpoint}}` => nama endpoint
- `{{tag}}` => kategori tag Swagger
- `{{summary}}` => deskripsi singkat endpoint
- `{{resource_name}}` => nama resource
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
 * @OA\Put(
 *      path="/{{endpoint}}/{id}",
 *      summary="{{summary}}",
 *      tags={"{{tag}}"},
 *      @OA\Parameter(
 *          name="id",
 *          in="path",
 *          description="{{resource_name}} ID",
 *          required=true,
 *          @OA\Schema(
 *              type="integer"
 *          )
 *      ),
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
 *          response=200,
 *          description="{{resource_name}} updated successfully"
 *      ),
 *      @OA\Response(
 *          response=404,
 *          description="{{resource_name}} not found"
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

## Example Usage
```php
/**
 * @OA\Put(
 *      path="/invoice-bills/{id}",
 *      summary="Update an invoice bill",
 *      tags={"Finance - Invoice Bills"},
 *      @OA\Parameter(
 *          name="id",
 *          in="path",
 *          description="Invoice Bill ID",
 *          required=true,
 *          @OA\Schema(
 *              type="integer"
 *          )
 *      ),
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
 *                      property="total",
 *                      type="number",
 *                      format="double",
 *                      description="Total"
 *                  ),
 *                  required={"id_type_transaction", "type", "total"},
 *                  example={
 *                      "id_type_transaction": 1,
 *                      "type": "transaction_full",
 *                      "total": 150000
 *                  }
 *              )
 *          )
 *      ),
 *      @OA\Response(
 *          response=200,
 *          description="Invoice Bill updated successfully"
 *      ),
 *      @OA\Response(
 *          response=404,
 *          description="Invoice Bill not found"
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
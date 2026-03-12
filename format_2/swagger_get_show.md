# GET - Get Resource by ID

## Overview
Endpoint untuk mengambil detail single resource berdasarkan ID.

## Endpoint
```
GET /{{endpoint}}/{id}
```

## Variables
- `{{endpoint}}` => nama endpoint (contoh: `resources`, `invoice-bills`, `users`)
- `{{tag}}` => kategori tag Swagger
- `{{summary}}` => deskripsi singkat endpoint
- `{{resource_name}}` => nama resource (contoh: `Resource`, `Invoice Bill`, `User`)

## Path Parameters
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| id | integer | Yes | Resource ID |

---

## Template Swagger
```php
/**
 * @OA\Get(
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
 *      @OA\Response(
 *          response=200,
 *          description="Successfully retrieved {{resource_name}}"
 *      ),
 *      @OA\Response(
 *          response=404,
 *          description="{{resource_name}} not found"
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
 * @OA\Get(
 *      path="/invoice-bills/{id}",
 *      summary="Get invoice bill by ID",
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
 *      @OA\Response(
 *          response=200,
 *          description="Successfully retrieved Invoice Bill"
 *      ),
 *      @OA\Response(
 *          response=404,
 *          description="Invoice Bill not found"
 *      ),
 *      @OA\Response(
 *          response=401,
 *          description="Unauthorized"
 *      ),
 *      security={{ "bearerAuth": {} }}
 * )
 */
```
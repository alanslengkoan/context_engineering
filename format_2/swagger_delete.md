# DELETE - Delete Resource

## Overview
Endpoint untuk menghapus resource berdasarkan ID.

## Endpoint
```
DELETE /{{endpoint}}/{id}
```

## Variables
- `{{endpoint}}` => nama endpoint
- `{{tag}}` => kategori tag Swagger
- `{{summary}}` => deskripsi singkat endpoint
- `{{resource_name}}` => nama resource

---

## Template Swagger
```php
/**
 * @OA\Delete(
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
 *          description="{{resource_name}} deleted successfully"
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
 * @OA\Delete(
 *      path="/invoice-bills/{id}",
 *      summary="Delete an invoice bill",
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
 *          description="Invoice Bill deleted successfully"
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
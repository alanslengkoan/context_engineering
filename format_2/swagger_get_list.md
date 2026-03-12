# GET - List Resources

## Overview
Endpoint untuk mengambil daftar semua resources dengan pagination dan filtering.

## Endpoint
```
GET /{{endpoint}}
```

## Variables
- `{{endpoint}}` => nama endpoint (contoh: `resources`, `invoice-bills`, `users`)
- `{{tag}}` => kategori tag Swagger (contoh: `Resource`, `Finance - Invoice Bills`)
- `{{summary}}` => deskripsi singkat endpoint

## Query Parameters
| Parameter | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| page | integer | No | 1 | Page number |
| per_page | integer | No | 10 | Items per page |
| search | string | No | - | Search keyword |
| status | string | No | - | Filter by status |

---

## Template Swagger
```php
/**
 * @OA\Get(
 *      path="/{{endpoint}}",
 *      summary="{{summary}}",
 *      tags={"{{tag}}"},
 *      @OA\Parameter(
 *          name="page",
 *          in="query",
 *          description="Page number",
 *          required=false,
 *          @OA\Schema(
 *              type="integer",
 *              default=1
 *          )
 *      ),
 *      @OA\Parameter(
 *          name="per_page",
 *          in="query",
 *          description="Items per page",
 *          required=false,
 *          @OA\Schema(
 *              type="integer",
 *              default=10
 *          )
 *      ),
 *      @OA\Parameter(
 *          name="search",
 *          in="query",
 *          description="Search keyword",
 *          required=false,
 *          @OA\Schema(
 *              type="string"
 *          )
 *      ),
 *      @OA\Response(
 *          response=200,
 *          description="Successfully retrieved list"
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
 *      path="/invoice-bills",
 *      summary="Get list of invoice bills",
 *      tags={"Finance - Invoice Bills"},
 *      @OA\Parameter(
 *          name="page",
 *          in="query",
 *          description="Page number",
 *          required=false,
 *          @OA\Schema(
 *              type="integer",
 *              default=1
 *          )
 *      ),
 *      @OA\Parameter(
 *          name="per_page",
 *          in="query",
 *          description="Items per page",
 *          required=false,
 *          @OA\Schema(
 *              type="integer",
 *              default=10
 *          )
 *      ),
 *      @OA\Parameter(
 *          name="search",
 *          in="query",
 *          description="Search keyword",
 *          required=false,
 *          @OA\Schema(
 *              type="string"
 *          )
 *      ),
 *      @OA\Response(
 *          response=200,
 *          description="Successfully retrieved list"
 *      ),
 *      @OA\Response(
 *          response=401,
 *          description="Unauthorized"
 *      ),
 *      security={{ "bearerAuth": {} }}
 * )
 */
```
# PUT - Update Resource (With File)

## Overview
Endpoint untuk update resource dengan file upload menggunakan multipart/form-data.
Menggunakan method spoofing (POST dengan _method=PUT).

## Endpoint
```
POST /{{endpoint}}/{id}?_method=PUT
```

## Variables
- `{{endpoint}}` => nama endpoint
- `{{tag}}` => kategori tag Swagger
- `{{summary}}` => deskripsi singkat endpoint
- `{{resource_name}}` => nama resource
- `{{properties}}` => daftar property sesuai kebutuhan
- `{{required_fields}}` => daftar field yang wajib diisi

## Content-Type
```
multipart/form-data
```

## Note
Karena multipart/form-data tidak support PUT method secara native, 
gunakan POST dengan parameter `_method=PUT` untuk method spoofing.

---

## Template Swagger
```php
/**
 * @OA\Post(
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
 *      @OA\Parameter(
 *          name="_method",
 *          in="query",
 *          description="HTTP Method",
 *          required=true,
 *          @OA\Schema(
 *              type="string",
 *              default="PUT"
 *          )
 *      ),
 *      @OA\RequestBody(
 *          required=true,
 *          @OA\MediaType(
 *              mediaType="multipart/form-data",
 *              @OA\Schema(
 *                  type="object",
 *                  {{properties}}
 *                  required={{required_fields}}
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
 * @OA\Post(
 *      path="/areas/{id}",
 *      summary="Update an area",
 *      tags={"Operation - Area"},
 *      @OA\Parameter(
 *          name="id",
 *          in="path",
 *          description="Area ID",
 *          required=true,
 *          @OA\Schema(
 *              type="integer"
 *          )
 *      ),
 *      @OA\Parameter(
 *          name="_method",
 *          in="query",
 *          description="HTTP Method",
 *          required=true,
 *          @OA\Schema(
 *              type="string",
 *              default="PUT"
 *          )
 *      ),
 *      @OA\RequestBody(
 *          required=true,
 *          @OA\MediaType(
 *              mediaType="multipart/form-data",
 *              @OA\Schema(
 *                  type="object",
 *                  @OA\Property(
 *                      property="id_sub_block",
 *                      type="integer",
 *                      description="ID Sub Block",
 *                      example=1
 *                  ),
 *                  @OA\Property(
 *                      property="name",
 *                      type="string",
 *                      description="Nama Area",
 *                      example="Area Updated"
 *                  ),
 *                  @OA\Property(
 *                      property="map",
 *                      type="string",
 *                      format="binary",
 *                      description="File Peta Area"
 *                  ),
 *                  required={"id_sub_block", "name"}
 *              )
 *          )
 *      ),
 *      @OA\Response(
 *          response=200,
 *          description="Area Updated Successfully"
 *      ),
 *      @OA\Response(
 *          response=404,
 *          description="Area not found"
 *      ),
 *      @OA\Response(
 *          response=422,
 *          description="Validation error"
 *      ),
 *      security={{ "bearerAuth": {} }}
 * )
 */
```
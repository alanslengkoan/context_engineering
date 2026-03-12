# POST - Create Resource (With File)

## Overview
Endpoint untuk membuat resource baru dengan file upload menggunakan multipart/form-data.

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

## Content-Type
```
multipart/form-data
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

### Text Field Property
```php
@OA\Property(
    property="{{field_name}}",
    type="string",
    description="{{description}}",
    example="{{example_value}}"
),
```

### Number Field Property
```php
@OA\Property(
    property="{{field_name}}",
    type="number",
    format="double",
    description="{{description}}",
    example={{example_value}}
),
```

### File Property
```php
@OA\Property(
    property="{{field_name}}",
    type="string",
    format="binary",
    description="{{description}}"
),
```

---

## Example Usage
```php
/**
 * @OA\Post(
 *      path="/areas",
 *      summary="Add a new area",
 *      tags={"Operation - Area"},
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
 *                      example="Area 1"
 *                  ),
 *                  @OA\Property(
 *                      property="map",
 *                      type="string",
 *                      format="binary",
 *                      description="File Peta Area"
 *                  ),
 *                  @OA\Property(
 *                      property="status",
 *                      type="string",
 *                      description="Status Area",
 *                      example="potential"
 *                  ),
 *                  required={"id_sub_block", "name", "map", "status"}
 *              )
 *          )
 *      ),
 *      @OA\Response(
 *          response=201,
 *          description="Area Created Successfully"
 *      ),
 *      @OA\Response(
 *          response=422,
 *          description="Validation error"
 *      ),
 *      security={{ "bearerAuth": {} }}
 * )
 */
```
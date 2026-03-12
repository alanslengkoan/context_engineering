# Format Model

## Aturan Penamaan File
- Nama file model harus sesuai dengan nama tabel di database (tanpa akhiran 's')
- Nama file model harus menggunakan huruf kapital untuk setiap kata (PascalCase)
- Nama file model harus ditambahkan suffix `Model` di akhir nama file (ExampleModel.php)

## Variables
- `{{table}}` => ambil dari nama tabel di database pada saat membuat migration
- `{{primary_key}}` => ambil dari nama primary key di database pada saat membuat migration
- `{{fillable}}` => ambil dari nama column di database pada saat membuat migration, kecuali:
  - `created_by`
  - `updated_by`
  - `created_at`
  - `updated_at`

---

## Template

```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class {{model}} extends Model
{
    use HasFactory;

    protected $table = '{{table}}';

    protected $primaryKey = '{{primary_key}}';

    protected $fillable = [
        {{fillable}}
    ];

    protected static function booted()
    {
        static::creating(function ($row) {
            $row->created_by = auth()->user()->id;
        });

        static::updating(function ($row) {
            $row->updated_by = auth()->user()->id;
        });
    }
}
```
format for model

nama file model:
- Nama file model harus sesuai dengan nama tabel di database (tanpa akhiran 's')
- Nama file model harus menggunakan huruf kapital untuk setiap kata (PascalCase)
- Nama file model harus ditambahkan Model di akhir nama file (ExampleModel.php)

$table => ambil dari nama tabel di database pada saat membuat migration

$primaryKey => ambil dari nama primary key di database pada saat membuat migration

$fillable => ambil dari nama column di database pada saat membuat migration kecuali column yang berikut:
- created_by
- updated_by
- created_at
- updated_at

## Sample Format
```php
use HasFactory;

protected $table = 'example';

protected $primaryKey = 'id_example';

protected $fillable = [];

protected static function booted()
{
    static::creating(function ($row) {
        $row->created_by = auth()->user()->id;
    });

    static::updating(function ($row) {
        $row->updated_by = auth()->user()->id;
    });
}
```
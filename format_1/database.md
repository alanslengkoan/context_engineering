# Format Database Migration

## Aturan Penamaan Column
- Menggunakan format singular (tanpa akhiran 's')
- Menggunakan underscore sebagai pemisah kata (snake_case)
- Primary key menggunakan prefix `id_` + nama tabel

## Variables
- `{{table}}` => nama tabel di database (snake_case, singular)
- `{{primary_key}}` => `id_` + nama tabel (contoh: `id_example`)
- `{{columns}}` => daftar column sesuai kebutuhan (snake_case, singular)

## Required Columns
Setiap tabel wajib memiliki column berikut di bagian paling bawah sebelum penutup:

```php
$table->integer('created_by')->nullable();
$table->integer('updated_by')->nullable();
$table->timestamp('created_at')->useCurrent();
$table->timestamp('updated_at')->useCurrent()->useCurrentOnUpdate();
```

---

## Template

```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    public function up(): void
    {
        Schema::create('{{table}}', function (Blueprint $table) {
            $table->increments('{{primary_key}}');
            {{columns}}
            $table->integer('created_by')->nullable();
            $table->integer('updated_by')->nullable();
            $table->timestamp('created_at')->useCurrent();
            $table->timestamp('updated_at')->useCurrent()->useCurrentOnUpdate();
        });
    }

    public function down(): void
    {
        Schema::dropIfExists('{{table}}');
    }
};
```
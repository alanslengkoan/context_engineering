format for database

column name :
- Menggunakan format singular (tanpa akhiran 's')
- Menggunakan underscore untuk pemisah kata (snake_case)
- Primary key menggunakan prefix `id_` + nama tabel

requirement column format :
- $table->integer('created_by')->nullable();
- $table->integer('updated_by')->nullable();
- $table->timestamp('created_at')->useCurrent();
- $table->timestamp('updated_at')->useCurrent()->useCurrentOnUpdate();
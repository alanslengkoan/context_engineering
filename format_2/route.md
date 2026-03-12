# Format Route

## Variables
- `{{controller}}` => nama class controller (PascalCase + suffix `Controller`)
- `{{prefix}}` => nama prefix route (kebab-case, plural)

---

## Template

```php
Route::controller({{controller}}::class)->prefix('{{prefix}}')->group(function () {
    Route::get('/', 'index');
    Route::post('/', 'store');
    Route::get('/{id}', 'show');
    Route::put('/{id}', 'update');
    Route::delete('/{id}', 'destroy');
});
```
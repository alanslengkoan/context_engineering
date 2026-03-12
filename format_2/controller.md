# Format API Controller

## Variables
- `{{controller}}` => BankNCashController
- `{{module}}` => finance (nama sub-folder namespace, lowercase)
- `{{model}}` => BankNCash
- `{{request}}` => BankCashRequest
- `{{resource}}` => BankNCashResource
- `{{connection}}` => finance (nama koneksi database di `config/database.php`)
- `{{label}}` => Bank and Cash (label untuk pesan response)
- `{{fields}}` => [
    '$data->column = $request->column;'
  ]

---

## Template

```php
<?php

namespace App\Http\Controllers\api\{{module}};

use App\Classes\ApiResponseClass;
use App\Http\Controllers\Controller;
use App\Http\Requests\{{module}}\{{request}};
use App\Http\Resources\{{module}}\{{resource}};
use App\Models\{{module}}\{{model}};
use Illuminate\Support\Facades\DB;

class {{controller}} extends Controller
{
    public function index()
    {
        $data = {{model}}::latest()->get();

        return ApiResponseClass::sendResponse({{resource}}::collection($data), '{{label}} Retrieved Successfully');
    }

    public function store({{request}} $request)
    {
        DB::connection('{{connection}}')->beginTransaction();
        try {
            $data = new {{model}}();
            {{fields}}
            $data->save();

            DB::connection('{{connection}}')->commit();

            return ApiResponseClass::sendResponse($data, '{{label}} Created Successfully');
        } catch (\Exception $e) {
            return ApiResponseClass::rollback($e);
        }
    }

    public function show($id)
    {
        $data = {{model}}::find($id);

        return ApiResponseClass::sendResponse({{resource}}::make($data), '{{label}} Retrieved Successfully');
    }

    public function update($id, {{request}} $request)
    {
        DB::connection('{{connection}}')->beginTransaction();
        try {
            $data = {{model}}::find($id);
            {{fields}}
            $data->save();

            DB::connection('{{connection}}')->commit();

            return ApiResponseClass::sendResponse($data, '{{label}} Updated Successfully');
        } catch (\Exception $e) {
            return ApiResponseClass::rollback($e);
        }
    }

    public function destroy($id)
    {
        try {
            $data = {{model}}::find($id);

            $data->delete();

            return ApiResponseClass::sendResponse($data, '{{label}} Deleted Successfully');
        } catch (\Exception $e) {
            return ApiResponseClass::throw('Cannot delete data or it is being used', 409, $e->getMessage());
        }
    }
}
```
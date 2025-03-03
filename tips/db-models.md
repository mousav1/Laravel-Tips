### 1. Using DB Transactions

DB transactions ensure that a series of database operations execute atomically—either all succeed or none do—maintaining data integrity.

```php
use Illuminate\Support\Facades\DB;

DB::transaction(function () use ($request) {
    $order = Order::create($request->all());
    Payment::create([
        'order_id' => $order->id,
        'amount'   => $order->total,
    ]);
});
```


### 2. Using firstOrCreate()

With `firstOrCreate()`, you can search for the first record matching specific attributes or create it if it doesn't exist.  


```php
<?php

namespace App\Http\Controllers;

use App\Models\Category;
use Illuminate\Http\Request;
use Illuminate\Support\Str;

class CategoryController extends Controller
{
    public function example(Request $request)
    {
        $category = Category::firstOrCreate(
            ['name' => $request->name],
            ['slug' => Str::slug($request->name)]
        );

        return $category;
    }
}
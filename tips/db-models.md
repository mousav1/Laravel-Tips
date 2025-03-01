### Using DB Transactions

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

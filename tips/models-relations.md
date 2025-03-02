### Aggregating Relationship Data with Eloquent

Use Eloquent’s aggregation methods to retrieve related data along with aggregate values. For example, you can load related models, count them, and compute the minimum, maximum, or average of a specific column—all in one query.

```php
$categories = Category::with('products')
    ->withCount('products')
    ->withMin('products', 'price')
    ->withMax('products', 'price')
    ->withAvg('products', 'price')
    ->get();

// Now each category model will have:
// - "products" relationship loaded.
// - "products_count" attribute.
// - "products_min_price" attribute.
// - "products_max_price" attribute.
// - "products_avg_price" attribute.

```


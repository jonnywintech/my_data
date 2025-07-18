Sortiranje tabela na frontendu kada se koristi pivot tabela i ima vise istih records 

```php

public function getTableRecords(): \Illuminate\Database\Eloquent\Collection | \Illuminate\Contracts\Pagination\Paginator | \Illuminate\Contracts\Pagination\CursorPaginator

{
	$records = parent::getTableRecords();

	return $records->unique('author_id');
}
```
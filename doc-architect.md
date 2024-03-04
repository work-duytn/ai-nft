# xử lý 1 request thông thường


```mermaid
flowchart TB
client-->A
A[Request] --> B[Check Authentication]
B --> C[Check Author]
C --> D[Validation]
D --> E["Process Raw Request Data(service)"]
E --> F["Update Database(repository)"]
F --> G["Response (JSON)"]	--> client
```
-   Check Authen: sử dụng middleware mặc định của Laravel
-   Check Authorization: đơn giản nhất sử dụng [ACL](https://laravel.com/docs/10.x/authorization) mặc định của Laravel 
-   Validation: sử dụng [Form Request](https://laravel.com/docs/10.x/validation#form-request-validation) của Laravel 
-   Process Raw data: tách ra thành các class riêng gọi là services -> nhớ luôn phải tạo interface và inject interface đó vào trong controller 
-   Tương tác với database: Sử dụng repository, inject vào service.

## Ví dụ
CRUD liên quan tới Book (title, author)

1. Tạo migration, controller, model và route
2. Áp middleware cho Authentication và authorize (nếu có)
```php
Route::group(['middleware' => 'auth'], function () {
    Route::resource('/books', 'BooksController');
});
```
3. Dùng request để validate
php artisan make:request CreateBookRequest
php artisan make:request EditBookRequest
4. 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc1NDQzODU0MCwtOTQ2MzI3NjU0XX0=
-->
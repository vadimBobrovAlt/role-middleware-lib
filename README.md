# Role Middleware

## Описание

Это библиотека предоставляет middleware для проверки ролей пользователя. С помощью этого middleware вы можете управлять доступом к различным маршрутам вашего приложения на основе ролей пользователя.

### Подключение

Чтобы подключить middleware для проверки ролей, добавьте следующий код в вашем `bootstrap/app.php`:

```php
->withMiddleware(function (Middleware $middleware) {
    $middleware->alias([
        'role' => RoleMiddleware::class
    ]);
});
```

### Использование

После подключения middleware вы можете использовать его в ваших маршрутах следующим образом:
```php
Route::middleware(['role:admin,editor')->group(function () {
    Route::get('/admin', [AdminController::class, 'index']);
    Route::get('/editor', [EditorController::class, 'index']);
});
```




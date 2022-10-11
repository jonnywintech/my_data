Route::group(['middleware'=>'verified'])

Route::group([
    'middleware' => 'auth'
], function () {
    Route::post('/logout', [AuthController::class, 'logout']);
    Route::get('/email/verify', [AuthController::class, 'getEmailVerificationNotice'])->name('verification.notice');

    Route::get('/email/verify/{id}/{hash}', [AuthController::class, 'verifyEmail'])->middleware(['signed'])->name('verification.verify');
});
# Attach Detach - vezivanje pivot tabela many to many u relationship manageru


primer koda u relationship manageru
```php
->headerActions([
     Tables\Actions\AttachAction::make()->form(fn(AttachAction $action) => [
                    Forms\Components\Select::make('author_id')
                        ->label('Attach author')
                        ->options(function () {
                            $articleId = $this->getOwnerRecord()->id;

                            return \App\Models\Author::whereNotIn('id', function ($query) use ($articleId) {
                                $query->select('author_id')
                                    ->from('article_authors')
                                    ->where('article_id', $articleId);
                            })->pluck('full_name', 'id');
                        })
                        ->multiple()
                        ->preload()
                        ->searchable()
                ])
                    ->action(function (array $data) {
                        // Access the parent record through the RelationManager
                        $record = $this->getOwnerRecord();

                        $authorIds = $data['author_id']; // This will be an array since multiple() is used

                        // Manual insertion into pivot table
                        foreach ($authorIds as $authorId) {
                            \Illuminate\Support\Facades\DB::table('article_authors')->insert([
                                'article_id' => $record->id,
                                'author_id' => $authorId,
                                'created_at' => now(),
                                'updated_at' => now(),
                            ]);
                        }

                        // Optional: Send a success notification
                        \Filament\Notifications\Notification::make()
                            ->title('Authors attached successfully')
                            ->success()
                            ->send();
                    })->label('Add existing user'),
            ]) 
])
```


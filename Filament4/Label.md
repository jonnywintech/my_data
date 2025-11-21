# Prevodjenje Filament4 Label komponenti

  ```php
  protected function getHeaderActions(): array
    {
        return [
            CreateAction::make()
                ->label(__('Create Appointment')),
        ];
    }
```
prevodi kompletan model
```php
    
    public static function getModelLabel(): string
    {
        return __('Appointment');
    }
```
prevod samo navigaciju
```php
    public static function getNavigationLabel(): string
    {
        return __('Appointments');
    }
```

prevod relacija 
```php

    public function table(Table $table): Table
    {
        return $table
            ->heading(__('Services'))
            ->columns([
                TextColumn::make('name')
                    ->label(__('Name'))
                    ->searchable(),
            ])
            ->headerActions([
                CreateAction::make()
                    ->label(__('Add Service')),
            ]);
    }
```
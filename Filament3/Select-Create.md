# Za kreiranje i slekt opcija u jednom

Kreiranje Selektora i dodavanje nove opcije ukoliko nepostoji

```php
      Forms\Components\Select::make('affiliations')
                    ->label('Affiliations')
                    ->relationship('affiliations', 'name')
                    ->multiple()
                    ->preload()
                    ->searchable()
                    ->createOptionForm([
                        Forms\Components\TextInput::make('name')
                            ->required()
                            ->columnSpanFull(),
                    ])
                    ->columnSpanFull(),
```
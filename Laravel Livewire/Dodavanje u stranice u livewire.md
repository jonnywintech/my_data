Da bi se stranica dodala u livewire da se ponasa kao react SPA

potrebno je u linkovima dodati `wire:navigate`
ova komanda u htmx omogucava ucitavanje stranice kao SPA

primeri

```php
 <a wire:navigate
                            class="font-medium py-3 md:py-6 {{ request()->is('/') ? 'text-blue-600 dark:text-blue-500' : 'text-gray-500' }} dark:focus:outline-none dark:focus:ring-1 dark:focus:ring-gray-600"
                            href="/" aria-current="page">Home</a>
```
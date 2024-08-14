kada sa jedne stranice treba da se updejtuje sadrzaj i da druge komponente informisu o sadrzaju i urade re-render sadrzaja potrebno je sledece.

- dodati `dispatch`
u primeru imamo addQuantity koja povecava sadrzaj korpe ali na navbaru nevidimo promene te je potrebno updejtovati i navbar kada se desi promena u korpi
```php
 public function addQuantity(int $id): void
    {
        $this->cart_items = CartManagment::incrementQuantityToCartItem($id);
        $this->grand_total = CartManagment::calculateGrandTotal($this->cart_items);
        $this->dispatch('update-cart-count', total_count: array_sum(array_column($this->cart_items, 'quantity')))->to(Navbar::class);
    }
```

A onda u navbar kontroleru imamo Event listener koji izgleda ovako

```php
use Livewire\Attributes\On;

 #[On('update-cart-count')]
    public function updateCartCount(int $total_count): void
    {
        $this->total_count = $total_count;
    }
```
`#` nije komentar vec listener

Ceo primer navbara
```php
<?php

namespace App\Livewire\Partials;

use App\Helpers\CartManagment;
use Livewire\Attributes\On;
use Livewire\Component;

class Navbar extends Component
{

    public int $total_count = 0;
    public function mount(): void
    {
        $this->total_count = array_sum(array_column(CartManagment::getCartItemsFromCookie(), 'quantity'));
    }
    
    #[On('update-cart-count')]
    public function updateCartCount(int $total_count): void
    {
        $this->total_count = $total_count;
    }

    
    public function render()
    {
        return view('livewire.partials.navbar');
    }
}

```
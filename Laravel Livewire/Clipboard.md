copying text to clipboard button

logic
```php
<?php

namespace App\Livewire\Components;

use Livewire\Component;

class ArticleActions extends Component
{
    public $slug;
    public $link;

    public function mount(string $slug)
    {
        $this->slug = $slug;
        $link = route('article.show', $this->slug);

        $this->link = $link;
    }
    public function copyArticleLink()
    {
       $this->dispatch('notification', [
            'message' => 'Link copied to clipboard!',
            'type' => 'success'
        ]);
    }

    public function render()
    {
        return view('livewire.components.article-actions');
    }
}

```
blade

```html
<!-- Trigger Button -->
<button onclick="navigator.clipboard.writeText('{{$link}}')" wire:click="copyArticleLink" type="button"
    class="w-full flex items-center gap-x-3.5 py-2 px-3 rounded-lg text-sm text-custom-dark-grey hover:bg-gray-100 focus:outline-none focus:bg-gray-100 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-gray-300 dark:focus:bg-gray-700">
    <svg class="w-4 h-4" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
        stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path>
        <path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path>
    </svg>
    Copy Link
</button>

```

### trigger notification

logic
```php
<?php

namespace App\Livewire\Components;

use Livewire\Component;

class NotificationPopup extends Component
{
    public function render()
    {
        return view('livewire.components.notification-popup');
    }
}

```
blade
```html
<div
    x-data="{ show: false, message: '', type: 'success' }"
    @notification.window="
        message = $event.detail.at(0).message || 'Done!';
        type = $event.detail.at(0).type || 'success';
        show = true;
        setTimeout(() => show = false, 3000);
    "
    x-show="show"
    x-transition:enter="transition ease-out duration-300"
    x-transition:enter-start="opacity-0 translate-y-2"
    x-transition:enter-end="opacity-100 translate-y-0"
    x-transition:leave="transition ease-in duration-200"
    x-transition:leave-start="opacity-100 translate-y-0"
    x-transition:leave-end="opacity-0 translate-y-2"
    x-cloak
    class="fixed bottom-5 right-5 z-50 max-w-sm w-full px-4 py-2 rounded-lg text-white shadow-md"
    :class="{
        'bg-green-500': type === 'success',
        'bg-red-500': type === 'error',
        'bg-yellow-500': type === 'warning',
        'bg-blue-500': type === 'info',
    }"
>
    <span x-text="message"></span>
</div>

```
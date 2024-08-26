Template Notifikacija koje nestaju posle 3 sekunde


livewire controller
```php
	public array $notifications = [];

    public function addNotification(string $type, string $message): void
    {
        $this->notifications[] = [
            'type' => $type,
            'message' => $message,
            'id' => uniqid()
        ];
    }

    public function removeNotification($id)
    {
        $this->notifications = array_filter($this->notifications, function ($notification) use ($id) {
            return $notification['id'] !== $id;
        });
    }

	/// poziva se komandom 
	$this->addNotification('error', 'Current password is incorrect.');
	////

```

## blade 

```php
  <!-- Notifications -->
        <div class="fixed bottom-0 right-0 z-50 p-6 space-y-4" x-data="{ notifications: @entangle('notifications') }">
            <template x-for="notification in notifications" :key="notification.id">
                <div class="p-4 bg-white border rounded-xl shadow-sm" x-init="setTimeout(() => $wire.removeNotification(notification.id), 3000)"
                    :class="{
                        'border-green-200': notification.type === 'success',
                        'border-red-200': notification
                            .type === 'error'
                    }"
                    x-show="true" x-transition:enter="transition ease-out duration-300"
                    x-transition:enter-start="opacity-0 transform scale-90"
                    x-transition:enter-end="opacity-100 transform scale-100"
                    x-transition:leave="transition ease-in duration-300"
                    x-transition:leave-start="opacity-100 transform scale-100"
                    x-transition:leave-end="opacity-0 transform scale-90">
                    <div class="flex items-center space-x-3">
                        <div class="flex-1">
                            <p class="text-sm font-medium"
                                :class="{
                                    'text-green-800': notification.type === 'success',
                                    'text-red-800': notification
                                        .type === 'error'
                                }"
                                x-text="notification.message"></p>
                        </div>
                        <button @click="$wire.removeNotification(notification.id)"
                            class="text-gray-400 hover:text-gray-500">
                            <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                    d="M6 18L18 6M6 6l12 12" />
                            </svg>
                        </button>
                    </div>
                </div>
            </template>
        </div>
```
#### U pozadini se koristi alpine.js koji komunicira sa livewireom



### Ceo primer Klase
```php
<?php

namespace App\Livewire;

use App\Models\User;
use Livewire\Component;
use Illuminate\Validation\Rule;
use Illuminate\Support\Facades\Hash;

class MyAccount extends Component
{
    public string $name, $email, $old_password, $new_password, $new_password_confirm;
    public array $notifications = [];

    public function mount()
    {
        $user = auth()->user();
        $this->name = $user->name;
        $this->email = $user->email;
    }

    public function updateInfo()
    {
        $user = auth()->user();

        $data = $this->validate([
            'name' => 'required|string|min:3|max:255',
            'email' => 'required|string|min:3|max:255|email|' . Rule::unique(User::class)->ignore($user->id),
        ]);

        if ($user->name === $data['name'] && $user->email === $data['email']) {
            $this->addNotification('error', 'Make changes to data before saving.');
            return;
        }

        $user->update(['name' => $this->name, 'email' => $this->email]);

        $this->addNotification('success', 'Successfully updated user info.');
    }

    public function updatePassword()
    {
        $this->validate([
            'old_password' => 'required|string|min:3|max:255',
            'new_password' => 'required|string|min:3|max:255',
            'new_password_confirm' => 'required|string|same:new_password'
        ]);

        $user = auth()->user();

        if (Hash::check($this->old_password, $user->password)) {
            $user->password = Hash::make($this->new_password);
            $user->save();

            $this->addNotification('success', 'Successfully updated password.');
            $this->old_password = '';
            $this->new_password = '';
            $this->new_password_confirm = '';
        } else {
            $this->addNotification('error', 'Current password is incorrect.');
        }
    }

    public function addNotification(string $type, string $message): void
    {
        $this->notifications[] = [
            'type' => $type,
            'message' => $message,
            'id' => uniqid()
        ];
    }

    public function removeNotification($id)
    {
        $this->notifications = array_filter($this->notifications, function ($notification) use ($id) {
            return $notification['id'] !== $id;
        });
    }

    public function render()
    {
        return view('livewire.my-account');
    }
}

```




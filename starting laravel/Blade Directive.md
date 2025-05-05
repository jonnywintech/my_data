# Laravel 12 and Livewire Blade Directives

## Core Laravel 12 Blade Directives

**Basic Control Structures:**

- `@if`, `@elseif`, `@else`, `@endif` - Conditional rendering
- `@unless`, `@endunless` - Inverse conditional
- `@isset`, `@endisset` - Check if variable is set
- `@empty`, `@endempty` - Check if variable is empty
- `@foreach`, `@endforeach` - Loop through arrays/collections
- `@forelse`, `@empty`, `@endforelse` - Loop with fallback for empty collections
- `@for`, `@endfor` - Traditional for loop
- `@while`, `@endwhile` - While loop
- `@switch`, `@case`, `@break`, `@default`, `@endswitch` - Switch statement

**Template Structure:**

- `@extends` - Inherit from a layout
- `@section`, `@endsection` - Define content sections
- `@yield` - Display content of a section
- `@stack`, `@push`, `@endpush` - Stack content for later use
- `@include` - Include another template
- `@includeIf` - Conditionally include a template
- `@includeWhen` - Include a template when a condition is true
- `@includeUnless` - Include a template unless a condition is true
- `@each` - Render a template for each item in a collection
- `@once`, `@endonce` - Include content only once per rendering cycle
- `@component`, `@endcomponent` - Create reusable components
- `@slot`, `@endslot` - Define named slots for components

**Others:**

- `@csrf` - Generate CSRF token field
- `@method` - Spoof HTTP methods for forms
- `@php`, `@endphp` - Execute PHP code
- `@json` - Output JSON-encoded content
- `@class` - Conditionally apply CSS classes
- `@checked`, `@selected`, `@disabled` - Form helpers
- `@props` - Define component props
- `@error`, `@enderror` - Display validation errors

## Livewire Directives

**Core Livewire Directives:**

- `@livewire` - Mount a Livewire component
- `@livewireScripts` - Include Livewire JavaScript
- `@livewireStyles` - Include Livewire CSS
- `@this` - Reference to the current Livewire component
- `wire:model` - Two-way data binding
- `wire:model.live` - Real-time data binding (updates on every keystroke)
- `wire:model.blur` - Update on blur event
- `wire:model.defer` - Defer updating until form submission

**Event Handling:**

- `wire:click` - Handle click events
- `wire:submit` - Handle form submission
- `wire:keydown` - Handle keydown events
- `wire:keyup` - Handle keyup events
- `wire:mouseenter` - Handle mouseenter events
- `wire:mouseleave` - Handle mouseleave events

**Loading States:**

- `wire:loading` - Show during loading
- `wire:loading.delay` - Show after a delay
- `wire:loading.class` - Add class during loading
- `wire:loading.attr` - Add attribute during loading
- `wire:loading.remove` - Remove during loading
- `wire:target` - Target specific actions for loading states

**Polling and Refreshing:**

- `wire:poll` - Refresh component at interval
- `wire:poll.visible` - Poll only when visible
- `wire:poll.keep-alive` - Keep polling even when not visible
- `wire:init` - Run action when component initializes

**Modifiers:**

- `wire:ignore` - Ignore updates to an element
- `wire:key` - Provide a unique key for DOM diffing
- `wire:dirty` - Track dirty state of inputs
- `wire:confirm` - Show confirmation dialog
- `wire:navigate` - Use SPA navigation
- `wire:transition` - Apply transitions to elements

These directives provide powerful tools for building interactive, dynamic interfaces with Laravel 12 and Livewire. The combination allows you to create reactive applications without writing a lot of JavaScript.

### In Details Basic Control Structures

#### @if, @elseif, @else, @endif

```blade
@if ($condition)
    This will display if condition is true
@elseif ($anotherCondition)
    This will display if the first condition is false but the second is true
@else
    This will display if all conditions are false
@endif
```

These directives provide conditional rendering in your templates based on PHP conditions. They work just like standard PHP if/else statements but with cleaner syntax.

#### @unless, @endunless

```blade
@unless ($user->isAdmin())
    You are not an administrator.
@endunless
```

The `@unless` directive is essentially the inverse of `@if` - it renders content when a condition evaluates to false, providing a more readable alternative to `@if (!$condition)`.

#### @isset, @endisset

```blade
@isset($variable)
    The $variable is defined and not null.
@endisset
```

This directive checks if a variable is defined and not null, using PHP's `isset()` function. It's useful for safely accessing potentially undefined variables.

#### @empty, @endempty

```blade
@empty($collection)
    The collection is empty.
@endempty
```

This checks if a variable is "empty" according to PHP's `empty()` function, rendering content if the variable is empty, zero, null, or an empty collection.

#### @foreach, @endforeach

```blade
@foreach ($users as $user)
    <p>{{ $user->name }}</p>
@endforeach
```

Iterates through arrays or collections, providing a clean way to loop through data and render content for each item.

#### @forelse, @empty, @endforelse

```blade
@forelse ($users as $user)
    <p>{{ $user->name }}</p>
@empty
    <p>No users found.</p>
@endforelse
```

Similar to `@foreach` but with built-in handling for empty collections, eliminating the need for a separate check before the loop.

#### @for, @endfor

```blade
@for ($i = 0; $i < 10; $i++)
    The current value is {{ $i }}
@endfor
```

Traditional for loop construct that works exactly like PHP's for loop, useful when you need precise control over iterations.

#### @while, @endwhile

```blade
@while ($condition)
    <p>I'm looping until the condition is false.</p>
@endwhile
```

Creates a loop that continues as long as the specified condition remains true, similar to PHP's while loop.

#### @switch, @case, @break, @default, @endswitch

```blade
@switch($value)
    @case(1)
        First case...
        @break
    @case(2)
        Second case...
        @break
    @default
        Default case...
@endswitch
```

Provides a cleaner alternative to multiple if/elseif statements when comparing a single value against multiple possible matches.

### Template Structure

#### @extends

```blade
@extends('layouts.app')
```

Specifies that the current template inherits from a parent layout, which is the foundation of template inheritance in Laravel.

#### @section, @endsection

```blade
@section('content')
    <p>This content will be placed in the content section.</p>
@endsection
```

Defines a block of content that will be inserted into the corresponding `@yield` directive in the parent layout.

#### @yield

```blade
@yield('content', 'Default content')
```

Used in parent layouts to specify where child template's content should be inserted. The second parameter is an optional default value shown if the section isn't defined.

#### @stack, @push, @endpush

```blade
<!-- In a layout file -->
@stack('scripts')

<!-- In a child view -->
@push('scripts')
    <script src="example.js"></script>
@endpush
```

Allows you to push content into a named stack from various templates, useful for aggregating CSS or JavaScript in a specified location.

#### @include

```blade
@include('shared.errors')
```

Imports another Blade template into the current one. Variables available in the parent template are also available to the included template.

#### @includeIf

```blade
@includeIf('view.name', ['data' => $data])
```

Includes a template only if it exists, preventing errors if the template file is missing.

#### @includeWhen

```blade
@includeWhen($boolean, 'view.name', ['data' => $data])
```

Conditionally includes a template if the first argument evaluates to true.

#### @includeUnless

```blade
@includeUnless($boolean, 'view.name', ['data' => $data])
```

Includes a template unless the first argument evaluates to true - the inverse of `@includeWhen`.

#### @each

```blade
@each('view.name', $collection, 'variable', 'view.empty')
```

Efficiently renders a template for each element in a collection, with an optional fallback template for empty collections.

#### @once, @endonce

```blade
@once
    <script>
        // This JavaScript will only be included once per rendering cycle
    </script>
@endonce
```

Ensures the enclosed content is only rendered once during a rendering cycle, useful for avoiding duplicate CSS or JavaScript declarations.

#### @component, @endcomponent

```blade
@component('components.alert')
    <strong>Whoops!</strong> Something went wrong!
@endcomponent
```

Creates reusable components with slots, essential for building modular interfaces.

#### @slot, @endslot

```blade
@component('components.alert')
    @slot('title')
        Alert Title
    @endslot

    Alert content here.
@endcomponent
```

Defines named slots within components, allowing you to inject different content into specific areas of a component.

### Others

#### @csrf

```blade
<form method="POST" action="/profile">
    @csrf
    <!-- Form fields -->
</form>
```

Generates a hidden input field containing a CSRF token that Laravel uses to protect your application from cross-site request forgery attacks.

#### @method

```blade
<form action="/posts/{{ $post->id }}" method="POST">
    @method('PUT')
    @csrf
    <!-- Form fields -->
</form>
```

Adds a hidden _method field to spoof HTTP methods that aren't supported by HTML forms (PUT, PATCH, DELETE), making RESTful controller design possible.

#### @php, @endphp

```blade
@php
    $variable = 'value';
    $data = doSomething();
@endphp
```

Executes arbitrary PHP code within your template, useful for complex logic that can't be expressed with other Blade directives.

#### @json

```blade
<script>
    var data = @json($dataArray);
    var data2 = @json($dataArray, JSON_PRETTY_PRINT);
</script>
```

Safely converts a PHP variable to JSON and escapes all necessary characters, perfect for passing data to JavaScript.

#### @class

```blade
<div @class([
    'p-4',
    'bg-red-500' => $errors->has('email'),
    'bg-green-500' => !$errors->has('email')
])></div>
```

Conditionally apply CSS classes, providing a clean syntax for dynamic class definitions.

#### @checked, @selected, @disabled

```blade
<input type="checkbox" name="active" value="1" @checked(old('active', $user->active))>

<select name="country">
    <option value="US" @selected(old('country', $user->country) == 'US')>United States</option>
    <option value="CA" @selected(old('country', $user->country) == 'CA')>Canada</option>
</select>

<button type="submit" @disabled($errors->isNotEmpty())>Submit</button>
```

Form helpers that conditionally add the `checked`, `selected`, or `disabled` attributes to form elements based on a boolean condition.

#### @props

```blade
@props(['type' => 'info', 'message'])

<div class="alert alert-{{ $type }}">
    {{ $message }}
</div>
```

Defines component props with optional default values, making components more reusable and customizable.

#### @error, @enderror

```blade
<input id="email" type="email" name="email" value="{{ old('email') }}">

@error('email')
    <div class="alert alert-danger">{{ $message }}</div>
@enderror
```

Conveniently displays validation error messages for a specific form field.

## Livewire Directives

### Core Livewire Directives

#### @livewire

```blade
@livewire('search-posts', ['initialQuery' => 'example'])
```

Mounts a Livewire component in your Blade templates, allowing you to embed dynamic, reactive components anywhere in your application.

#### @livewireScripts

```blade
<!DOCTYPE html>
<html>
<head>
    <!-- ... -->
    @livewireStyles
</head>
<body>
    <!-- ... -->
    @livewireScripts
</body>
</html>
```

Includes the necessary JavaScript assets for Livewire to function, typically placed right before the closing `</body>` tag.

#### @livewireStyles

```blade
<head>
    <!-- ... -->
    @livewireStyles
</head>
```

Includes the necessary CSS assets for Livewire, typically placed in the document's `<head>`.

#### @this

```blade
<button onclick="confirm('Are you sure?') && @this.delete()">Delete</button>
```

Provides a reference to the current Livewire component instance in JavaScript contexts, allowing direct method calls from JavaScript.

#### wire:model

```blade
<input type="text" wire:model="name">
```

Creates two-way data binding between input elements and Livewire component properties, automatically updating the component state when the input changes.

#### wire:model.live

```blade
<input type="text" wire:model.live="searchQuery">
```

Updates the component state on every keystroke, enabling real-time features like live search.

#### wire:model.blur

```blade
<input type="text" wire:model.blur="username">
```

Updates the component state when the input loses focus (on blur), reducing the number of server roundtrips for non-critical updates.

#### wire:model.defer

```blade
<input type="text" wire:model.defer="address">
```

Defers updating the component state until an action like form submission occurs, optimizing performance by batching updates.

### Event Handling

#### wire:click

```blade
<button wire:click="addToCart({{ $product->id }})">Add To Cart</button>
```

Triggers a component method when an element is clicked, enabling interactive UIs without writing JavaScript.

#### wire:submit

```blade
<form wire:submit="savePost">
    <!-- Form fields -->
    <button type="submit">Save</button>
</form>
```

Handles form submissions, preventing the default form submission and instead calling a component method.

#### wire:keydown

```blade
<input wire:keydown.enter="search" type="text">
```

Listens for keyboard events, optionally filtering by specific keys like enter, escape, or arrow keys.

#### wire:keyup

```blade
<input wire:keyup="updateSearchResults" type="text">
```

Similar to keydown but triggers after the key is released, useful for implementing type-ahead search or other keyboard-interactive features.

#### wire:mouseenter

```blade
<div wire:mouseenter="showTooltip">Hover over me</div>
```

Triggers a component method when the mouse enters an element, useful for tooltips and hover effects.

#### wire:mouseleave

```blade
<div wire:mouseleave="hideTooltip">Move mouse away</div>
```

Triggers a component method when the mouse leaves an element, complementing mouseenter for complete hover interaction.

### Loading States

#### wire:loading

```blade
<div wire:loading>
    Processing your request...
</div>
```

Shows an element only during component loading states, perfect for loading indicators.

#### wire:loading.delay

```blade
<div wire:loading.delay>
    <!-- Only shown after a short delay, preventing flicker for fast operations -->
    Loading...
</div>
```

Shows the loading element only after a short delay, preventing UI flicker for quick operations.

#### wire:loading.class

```blade
<button wire:click="save" wire:loading.class="opacity-50">
    Save
</button>
```

Adds a CSS class to an element during loading states, useful for visual feedback.

#### wire:loading.attr

```blade
<button wire:click="checkout" wire:loading.attr="disabled">
    Complete Purchase
</button>
```

Adds an attribute to an element during loading states, commonly used to disable buttons while processing.

#### wire:loading.remove

```blade
<span wire:loading.remove>Click to continue</span>
```

Removes an element during loading states, showing alternative content when an action is processing.

#### wire:target

```blade
<button wire:click="checkout">Checkout</button>

<div wire:loading wire:target="checkout">
    Processing payment...
</div>
```

Targets specific actions for loading states, allowing precise control over which loading indicators appear for which actions.

### Polling and Refreshing

#### wire:poll

```blade
<div wire:poll.2000ms>
    Current time: {{ now() }}
</div>
```

Automatically refreshes a component at a specified interval (defaulting to 2 seconds), useful for real-time updates.

#### wire:poll.visible

```blade
<div wire:poll.visible>
    <!-- Only polls when visible in the viewport -->
    Live data: {{ $liveData }}
</div>
```

Only polls when the element is visible in the viewport, optimizing performance and server load.

#### wire:poll.keep-alive

```blade
<div wire:poll.keep-alive>
    <!-- Continues polling even when the browser tab is not active -->
    Background updates: {{ $backgroundData }}
</div>
```

Continues polling even when the browser tab is not active, useful for critical updates that should continue in background tabs.

#### wire:init

```blade
<div wire:init="loadPosts">
    <!-- Content loaded after component initialization -->
</div>
```

Runs a component method when the component is initialized, useful for lazy-loading data after the initial render.

### Modifiers

#### wire:ignore

```blade
<div wire:ignore>
    <!-- Content that should not be updated during Livewire refreshes -->
    <script>
        initializeThirdPartyPlugin();
    </script>
</div>
```

Tells Livewire to ignore updates to an element, essential when integrating third-party JavaScript libraries.

#### wire:key

```blade
@foreach ($users as $user)
    <div wire:key="{{ $user->id }}">
        <!-- User content -->
    </div>
@endforeach
```

Provides a unique key for DOM diffing, improving performance and preventing issues when elements move around.

#### wire:dirty

```blade
<input wire:model="name" wire:dirty.class="border-red-500">
```

Tracks the "dirty" state of inputs (when they've been modified but not saved), useful for form validation UI.

#### wire:confirm

```blade
<button wire:click="delete" wire:confirm="Are you sure you want to delete this item?">
    Delete
</button>
```

Shows a confirmation dialog before performing an action, adding a safety check for destructive operations.

#### wire:navigate

```blade
<a href="/dashboard" wire:navigate>Dashboard</a>
```

Enables SPA-like navigation between pages without full page reloads, providing a smoother user experience.

#### wire:transition

```blade
<div wire:transition>
    <!-- Content with transition effects during updates -->
</div>
```

Applies CSS transitions to elements during updates, creating smoother visual transitions between state changes.
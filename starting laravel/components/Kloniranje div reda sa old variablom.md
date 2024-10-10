ovde je jedan od primera kako klonirati red. izuzetan primer kako se koristi `old` funkcija sa arrayom

takodje je moguce kloniranje sa `nodeClone(true)` koju preferam umesto innerHTML koje je naveden u primeru
```php
<div class="py-5">
    <div class="bg-red-400 text-center font-bold text-dark p-1">
        Section Title
    </div>
    <div class="border rounded-lg shadow overflow-hidden">
        <div class="divide-y-2 divide-blue-950">
            <div class="flex flex-col border rounded-lg shadow overflow-hidden row-container divide-y-2 divide-blue-950">
                <div class="flex divide-x-2 divide-blue-950 border-t-2 border-blue-950 text-center">
                    <div class="w-3/12 px-6 py-4 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center">
                        Column 1 Title
                    </div>
                    <div class="w-4/12 px-6 py-4 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center">
                        Column 2 Title
                    </div>
                    <div class="w-4/12 px-6 py-4 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center">
                        Column 3 Title
                    </div>
                    <div class="w-1/12 px-6 py-4 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center">
                        Action
                    </div>
                </div>

                <div class="flex divide-x-2 divide-blue-950 row-item">
                    <div class="w-3/12 px-6 py-4 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center text-start gap-1">
                        <input type="text" name="column_1[]" class="p-1 rounded column_1" value="{{ old('column_1')[0] ?? '' }}">
                        @component('components.validation-error', ['field' => 'column_1.0'])
                        @endcomponent
                    </div>
                    <div class="w-4/12 px-6 py-4 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center gap-1">
                        <label class="text-center text-xs" for="column_2">Column 2 Input Label:</label>
                        <input type="text" name="column_2[]" id="column_2" class="p-1 rounded column_2" value="{{ old('column_2')[0] ?? '' }}">
                        @component('components.validation-error', ['field' => 'column_2.0'])
                        @endcomponent
                    </div>
                    <div class="w-4/12 px-6 py-4 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center gap-1">
                        <textarea class="rounded p-1" name="column_3[]" cols="15" rows="5">{{ old('column_3')[0] ?? '' }}</textarea>
                        @component('components.validation-error', ['field' => 'column_3.0'])
                        @endcomponent
                    </div>
                    <div class="px-3 py-2 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center">
                        <button disabled class="remove-row disabled:cursor-not-allowed text-xs disabled:bg-gray-500 bg-red-500 hover:bg-red-700 text-white font-bold py-1 px-2 rounded m-2 text-right transition">
                            Remove
                        </button>
                    </div>
                </div>

                @if (old('column_1') >= 1)
                    @for ($i = 1; $i < count(old('column_2')); $i++)
                    <div class="flex divide-x-2 divide-blue-950 row-item">
                        <div class="w-3/12 px-6 py-4 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center text-start gap-1">
                            <input type="text" name="column_1[]" class="p-1 rounded column_1" value="{{ old('column_1')[$i] ?? '' }}">
                            @component('components.validation-error', ['field' => 'column_1.' . $i])
                            @endcomponent
                        </div>
                        <div class="w-4/12 px-6 py-4 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center gap-1">
                            <label class="text-center text-xs" for="column_2_{{ $i }}">Column 2 Input Label:</label>
                            <input type="text" name="column_2[]" id="column_2_{{ $i }}" class="p-1 rounded column_2" value="{{ old('column_2')[$i] ?? '' }}">
                            @component('components.validation-error', ['field' => 'column_2.' . $i])
                            @endcomponent
                        </div>
                        <div class="w-4/12 px-6 py-4 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center gap-1">
                            <textarea class="rounded p-1" name="column_3[]" cols="15" rows="5">{{ old('column_3')[$i] ?? '' }}</textarea>
                            @component('components.validation-error', ['field' => 'column_3.' . $i])
                            @endcomponent
                        </div>
                        <div class="px-3 py-2 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center">
                            <button class="remove-row bg-red-500 text-xs hover:bg-red-700 text-white font-bold py-1 px-2 rounded m-2 text-right transition">
                                Remove
                            </button>
                        </div>
                    </div>
                    @endfor
                @endif

                <div class="w-full flex justify-end order-last">
                    <button type="button" class="add-row bg-green-500 text-xs hover:bg-green-700 text-white font-bold py-2 px-4 rounded m-3 text-right transition">
                        Add Row
                    </button>
                </div>

                {{-- Dynamic Row Addition and Removal --}}
                <script>

                    const addRowButton = document.querySelector('.add-row');
                    const rowContainer = document.querySelector('.row-container');

                    addRowButton.addEventListener('click', function() {
                
                        const newRow = document.createElement('div');
                        newRow.classList.add('flex', 'divide-x-2', 'divide-blue-950', 'row-item');

                        newRow.innerHTML = `
                            <div class="w-3/12 px-6 py-4 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center text-start gap-1">
                                <input type="text" name="column_1[]" class="p-1 rounded column_1">
                            </div>
                            <div class="w-4/12 px-6 py-4 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center gap-1">
                                <label class="text-center text-xs" for="column_2">Column 2 Input Label:</label>
                                <input type="text" name="column_2[]" class="p-1 rounded column_2">
                            </div>
                            <div class="w-4/12 px-6 py-4 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center gap-1">
                                <textarea class="rounded p-1" name="column_3[]" cols="15" rows="5"></textarea>
                            </div>
                            <div class="px-3 py-2 whitespace-wrap text-sm font-medium text-dark flex flex-col justify-center">
                                <button class="remove-row bg-red-500 text-xs hover:bg-red-700 text-white font-bold py-1 px-2 rounded m-2 text-right transition">
                                    Remove
                                </button>
                            </div>
                        `;

                        rowContainer.insertBefore(newRow, addRowButton.parentElement);

                        newRow.querySelector('.remove-row').addEventListener('click', function() {
                            newRow.remove();
                        });
                    });

                    document.querySelectorAll('.remove-row').forEach(function(button) {
                        button.addEventListener('click', function() {
                            button.parentElement.parentElement.remove();
                        });
                    });
                </script>
            </div>
        </div>
    </div>
</div>

```
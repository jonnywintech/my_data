html verzija sa dropzonom za upload fajlova
izmeniti neke stvari oko minimalnog broja fajlova ako koristite
```html
                            <div class="flex flex-col">
                                <div class="flex items-center justify-center w-full px-6 py-4">
                                    <label id="dropzone" for="dropzone-file"
                                        class="flex flex-col items-center justify-center w-full h-64 border-2 border-gray-300 border-dashed rounded-lg cursor-pointer bg-gray-50 hover:bg-gray-100">
                                        <div class="flex flex-col items-center justify-center pt-5 pb-6">
                                            <svg class="w-8 h-8 mb-4 text-gray-800" aria-hidden="true"
                                                xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 20 16">
                                                <path stroke="currentColor" stroke-linecap="round"
                                                    stroke-linejoin="round" stroke-width="2"
                                                    d="M13 13h3a3 3 0 0 0 0-6h-.025A5.56 5.56 0 0 0 16 6.5 5.5 5.5 0 0 0 5.207 5.021C5.137 5.017 5.071 5 5 5a4 4 0 0 0 0 8h2.167M10 15V6m0 0L8 8m2-2 2 2" />
                                            </svg>
                                            <p class="mb-2 text-sm text-gray-800"><span class="font-semibold">Klikni da
                                                    uploaduješ</span> ili prevuci fajlove</p>
                                            <p class="text-xs text-gray-800">PDF, DOCX, PNG, JPG (Minimum 3 fajla)</p>
                                        </div>
                                        <input id="dropzone-file" type="file" multiple class="hidden"
                                            name="fajlovi[]" accept=".png, .jpg, .jpeg, .pdf, .doc, .docx"
                                            onchange="handleFiles(this.files)" />
                                    </label>

                                </div>

                                <!-- Display uploaded files here -->
                                <div id="file-preview" class="mt-4 flex flex-row px-6 py-4 gap-2 flex-wrap">
                                    @component('components.validation-error', ['field' => 'fajlovi'])
                                    @endcomponent
                                </div>

                                <script>
                                    const chekiranaObuka = document.querySelector('.obuka__chekirana');
                                    const radioSelektors = document.querySelectorAll('.potrebna__obuka');


                                    radioSelektors.forEach(selektor => {
                                        selektor.addEventListener('change', (e) => {

                                            if (e.target.value === 'da') {
                                                chekiranaObuka.classList.remove('hidden');
                                            } else {
                                                chekiranaObuka.classList.add('hidden');
                                            }
                                        })
                                    })

                                    let uploadedFiles = []; // Array to store uploaded files

                                    function handleFiles(files) {
                                        const newFiles = Array.from(files).filter(file =>
                                            !uploadedFiles.some(uploadedFile => uploadedFile.name === file.name)
                                        );

                                        const maxSize = 5 * 1024 * 1024; // 5MB
                                        const allowedFormats = ['image/png', 'image/jpeg', 'application/pdf', 'application/msword', 'application/vnd.openxmlformats-officedocument.wordprocessingml.document'];

                                        const validFiles = Array.from(files).filter(file => {
                                            if (!allowedFormats.includes(file.type)) {
                                                alert(`Unsupported format: ${file.name}`);
                                                return false;
                                            }
                                            if (file.size > maxSize) {
                                                alert(`File ${file.name} je prevelik/a. Maksimalna veličina je 5MB.`);
                                                return false;
                                            }
                                            return true;
                                        });

                                        if (uploadedFiles.length + newFiles.length < 3) {
                                            alert('Uploadujte najmanje 3 fajla.');
                                            return;
                                        }

                                        uploadedFiles = [...uploadedFiles, ...newFiles];
                                        renderFiles();
                                    }


                                    function renderFiles() {
                                        const preview = document.getElementById('file-preview');
                                        preview.innerHTML = ''; // Clear existing previews

                                        uploadedFiles.forEach((file, index) => {
                                            const fileReader = new FileReader();

                                            fileReader.onload = (e) => {
                                                const fileElement = document.createElement('div');
                                                fileElement.classList.add('flex', 'flex-wrap', 'align-middle', 'items-center', 'mb-2',
                                                    'p-2', 'bg-gray-100', 'rounded',
                                                    'shadow-sm', 'relative');

                                                if (file.type.startsWith('image/')) {
                                                    const img = document.createElement('img');
                                                    img.src = e.target.result;
                                                    img.classList.add('w-16', 'h-16', 'mr-4', 'rounded');
                                                    fileElement.appendChild(img);
                                                }

                                                const fileName = document.createElement('p');
                                                fileName.textContent = file.name;
                                                fileName.classList.add('text-gray-700', 'mr-4');
                                                fileElement.appendChild(fileName);

                                                // Create remove button (X)
                                                const removeButton = document.createElement('button');
                                                removeButton.textContent = '✕';
                                                removeButton.classList.add('text-red-500', 'hover:text-red-700', 'absolute', 'right-0',
                                                    'top-0', 'bottom-0', 'mr-2');
                                                removeButton.onclick = () => removeFile(index); // Attach remove function
                                                fileElement.appendChild(removeButton);

                                                preview.appendChild(fileElement);
                                            };

                                            fileReader.readAsDataURL(file);
                                        });
                                    }

                                    function removeFile(index) {
                                        uploadedFiles.splice(index, 1); // Remove the file from the array
                                        renderFiles(); // Re-render the file list
                                    }

                                    // Drag and Drop functionality
                                    const dropzone = document.getElementById('dropzone');

                                    dropzone.addEventListener('dragover', (e) => {
                                        e.preventDefault();
                                        dropzone.classList.add('bg-gray-200'); // Add hover effect
                                    });

                                    dropzone.addEventListener('dragleave', () => {
                                        dropzone.classList.remove('bg-gray-200'); // Remove hover effect
                                    });

                                    dropzone.addEventListener('drop', (e) => {
                                        e.preventDefault();
                                        dropzone.classList.remove('bg-gray-200'); // Remove hover effect

                                        const files = e.dataTransfer.files;
                                        handleFiles(files); // Handle dropped files
                                    });
                                </script>
                            </div>
```
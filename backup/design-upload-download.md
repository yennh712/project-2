# Backup: Design Upload/Download Code (ProductPage)

## Template Snippets (to restore later)

```126:201:src/components/ProductPage.vue
          <!-- File Upload -->
          <div class="form-section">
            <label class="form-label">Upload Design:</label>
            
            <!-- Custom File Upload Button -->
            <div class="file-upload-container">
              <input 
                ref="fileInput"
                type="file" 
                @change="handleUpload"
                accept="image/*"
                class="file-upload-input"
                id="file-upload"
              />
              <label for="file-upload" class="file-upload-button">
                <svg class="file-upload-icon" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12"></path>
                </svg>
                <span class="file-upload-text">Choose File</span>
              </label>
              <div v-if="selectedFileName" class="file-name">
                Selected: {{ selectedFileName }}
              </div>
            </div>
          </div>

          <!-- Action Buttons -->
          <div class="form-section" style="display: flex; gap: 1rem; flex-wrap: wrap;">
            <!-- Download Design Button -->
            <button 
              @click="downloadDesign"
              :disabled="!selectedFileName"
              class="download-button"
              style="
                padding: 0.75rem 1.5rem;
                background-color: #10b981;
                color: white;
                border-radius: 0.5rem;
                border: none;
                cursor: pointer;
                transition: background-color 0.2s;
                flex: 1;
                min-width: 150px;
              "
              :style="!selectedFileName ? 'background-color: #9ca3af; cursor: not-allowed;' : ''"
              @mouseover="selectedFileName && (this.style.backgroundColor='#059669')"
              @mouseout="selectedFileName && (this.style.backgroundColor='#10b981')"
            >
              <svg style="width: 1rem; height: 1rem; margin-right: 0.5rem; display: inline-block; vertical-align: middle;" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 10v6m0 0l-3-3m3 3l3-3m2 8H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"></path>
              </svg>
              Download Design
            </button>

          </div>
```

## Script Snippets (to restore later)

```208:429:src/components/ProductPage.vue
const selectedFileName = ref("");
const fileInput = ref(null);
let designImg = null;

const handleUpload = (e) => {
  const file = e.target.files[0];
  if (!file) return;
  selectedFileName.value = file.name;
  const reader = new FileReader();
  reader.onload = () => {
    designImg = new Image();
    designImg.onload = () => drawPreview();
    designImg.src = reader.result;
  };
  reader.readAsDataURL(file);
};

const drawPreview = () => { /* ... uses designImg to draw in print area ... */ };

const downloadDesign = async () => {
  if (!selectedFileName.value || !designImg || !mockupImage.value) {
    alert('Please upload a design first');
    return;
  }
  // compose mockup and design into a canvas, then download as PNG
};
```

## Styles (to restore later)

```264:336:src/style.css
.file-upload-container { /* ... */ }
.file-upload-input { /* ... */ }
.file-upload-button { /* ... */ }
.file-upload-button:hover { /* ... */ }
.file-upload-button:active { /* ... */ }
.file-upload-icon { /* ... */ }
.file-upload-text { /* ... */ }
.file-name { /* ... */ }
```

Notes:
- These snippets were removed per request. Restore them by reversing the edits in `src/components/ProductPage.vue` and re-adding the CSS in `src/style.css`.


# Ai-image-enhance.this website created by shrikant.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Image Enhancer Pro</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --primary: #6366f1;
            --primary-dark: #4f46e5;
            --secondary: #f43f5e;
            --dark: #1e293b;
            --light: #f8fafc;
            --gray: #94a3b8;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f1f5f9;
            margin: 0;
            padding: 0;
            color: var(--dark);
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
            border-bottom: 1px solid #e2e8f0;
            margin-bottom: 30px;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.5rem;
            font-weight: 600;
            color: var(--primary);
        }
        
        .logo i {
            font-size: 1.8rem;
        }
        
        .main-content {
            display: grid;
            grid-template-columns: 300px 1fr;
            gap: 30px;
        }
        
        .editor-container {
            background: white;
            border-radius: 12px;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
            padding: 20px;
            position: relative;
        }
        
        .image-preview {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
        
        .preview-area {
            position: relative;
            border-radius: 8px;
            overflow: hidden;
            background: #f8fafc;
            border: 2px dashed #cbd5e1;
            min-height: 400px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .preview-area.active {
            border-color: var(--primary);
        }
        
        .preview-image {
            max-width: 100%;
            max-height: 100%;
            display: none;
        }
        
        .before-after {
            display: flex;
            gap: 10px;
            margin-top: 20px;
        }
        
        .before-after img {
            width: 48%;
            border-radius: 8px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }
        
        .controls {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .control-group {
            background: white;
            border-radius: 8px;
            padding: 15px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }
        
        .control-group h3 {
            margin-top: 0;
            margin-bottom: 15px;
            font-size: 1rem;
            color: var(--dark);
        }
        
        .slider-control {
            margin-bottom: 15px;
        }
        
        .slider-control label {
            display: block;
            margin-bottom: 5px;
            font-size: 0.875rem;
            color: #64748b;
        }
        
        .slider-container {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .slider {
            flex-grow: 1;
            -webkit-appearance: none;
            height: 6px;
            border-radius: 3px;
            background: #e2e8f0;
            outline: none;
        }
        
        .slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 16px;
            height: 16px;
            border-radius: 50%;
            background: var(--primary);
            cursor: pointer;
        }
        
        .slider-value {
            width: 40px;
            text-align: center;
            font-size: 0.875rem;
            color: var(--dark);
        }
        
        .btn {
            padding: 10px 15px;
            border-radius: 6px;
            border: none;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.2s;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }
        
        .btn-primary {
            background: var(--primary);
            color: white;
        }
        
        .btn-primary:hover {
            background: var(--primary-dark);
        }
        
        .btn-secondary {
            background: var(--light);
            color: var(--dark);
            border: 1px solid #cbd5e1;
        }
        
        .btn-secondary:hover {
            background: #e2e8f0;
        }
        
        .btn-group {
            display: flex;
            gap: 10px;
        }
        
        .file-input {
            display: none;
        }
        
        .drop-message {
            text-align: center;
            padding: 30px;
            color: #64748b;
        }
        
        .drop-message i {
            font-size: 2.5rem;
            color: var(--primary);
            margin-bottom: 15px;
        }
        
        .drop-message p {
            margin: 0;
        }
        
        .preset-options {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
        }
        
        .preset-btn {
            padding: 8px;
            border-radius: 6px;
            background: #f8fafc;
            border: 1px solid #e2e8f0;
            cursor: pointer;
            transition: all 0.2s;
            text-align: center;
            font-size: 0.75rem;
        }
        
        .preset-btn:hover {
            border-color: var(--primary);
            color: var(--primary);
        }
        
        .preset-btn.active {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
        }
        
        .format-options {
            display: flex;
            gap: 10px;
        }
        
        .format-btn {
            padding: 8px 12px;
            border-radius: 6px;
            background: #f8fafc;
            border: 1px solid #e2e8f0;
            cursor: pointer;
            transition: all 0.2s;
            font-size: 0.75rem;
        }
        
        .format-btn.active {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
        }
        
        .loading-overlay {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(255,255,255,0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            gap: 15px;
            display: none;
            z-index: 10;
        }
        
        .spinner {
            width: 40px;
            height: 40px;
            border: 4px solid rgba(99, 102, 241, 0.2);
            border-radius: 50%;
            border-top-color: var(--primary);
            animation: spin 1s ease-in-out infinite;
        }
        
        @keyframes spin {
            to { transform: rotate(360deg); }
        }
        
        .history-item {
            display: flex;
            align-items: center;
            padding: 10px;
            border-radius: 6px;
            cursor: pointer;
            margin-bottom: 8px;
        }
        
        .history-item:hover {
            background: #f1f5f9;
        }
        
        .history-thumb {
            width: 40px;
            height: 40px;
            border-radius: 4px;
            object-fit: cover;
            margin-right: 10px;
        }
        
        .history-info {
            flex-grow: 1;
        }
        
        .history-info h4 {
            margin: 0;
            font-size: 0.875rem;
            font-weight: 500;
        }
        
        .history-info p {
            margin: 0;
            font-size: 0.75rem;
            color: #64748b;
        }
        
        .compare-slider {
            position: relative;
            width: 100%;
            height: 400px;
            overflow: hidden;
            border-radius: 8px;
        }
        
        .compare-slider img {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: contain;
        }
        
        .compare-before {
            z-index: 1;
            clip-path: inset(0 50% 0 0);
        }
        
        .compare-after {
            z-index: 2;
            clip-path: inset(0 0 0 50%);
        }
        
        .compare-handle {
            position: absolute;
            top: 0;
            bottom: 0;
            left: 50%;
            width: 4px;
            background: white;
            z-index: 3;
            cursor: ew-resize;
            transform: translateX(-2px);
            box-shadow: 0 0 10px rgba(0,0,0,0.2);
        }
        
        .compare-handle::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 30px;
            height: 30px;
            background: white;
            border-radius: 50%;
            transform: translate(-50%, -50%);
            box-shadow: 0 0 5px rgba(0,0,0,0.3);
        }
        
        .error-message {
            color: #dc2626;
            background: #fee2e2;
            padding: 10px;
            border-radius: 6px;
            margin-bottom: 15px;
            display: none;
        }
        
        .quality-indicator {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-top: 5px;
            font-size: 0.75rem;
            color: #64748b;
        }
        
        .quality-bar {
            flex-grow: 1;
            height: 4px;
            background: #e2e8f0;
            border-radius: 2px;
            overflow: hidden;
        }
        
        .quality-progress {
            height: 100%;
            background: var(--primary);
            width: 90%;
        }
        
        /* Ad containers */
        .ad-container {
            background: white;
            border-radius: 8px;
            padding: 10px;
            margin: 15px 0;
            text-align: center;
            border: 1px solid #e2e8f0;
        }
        
        .ad-label {
            font-size: 0.75rem;
            color: #64748b;
            margin-bottom: 5px;
            display: block;
        }
        
        .view-counter {
            font-size: 0.8rem;
            color: #64748b;
            text-align: center;
            margin-top: 10px;
            padding: 5px;
            background: #f8fafc;
            border-radius: 4px;
        }
        
        @media (max-width: 768px) {
            .main-content {
                grid-template-columns: 1fr;
            }
            
            .preset-options {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .ad-container {
                margin: 10px 0;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">
                <i class="fas fa-wand-magic-sparkles"></i>
                <span>AI Image Enhancer Pro</span>
            </div>
            <div>
                <button class="btn btn-secondary">
                    <i class="fas fa-user"></i> Sign In
                </button>
            </div>
        </header>
        
        <div class="main-content">
            <div class="controls">
                <div class="error-message" id="error-message">
                    <i class="fas fa-exclamation-circle"></i> 
                    <span id="error-text">Error loading image. Please try another file.</span>
                </div>
                
                <!-- Top Ad Container -->
                <div class="ad-container">
                    <span class="ad-label">Advertisement</span>
                    <!-- Adsterra Ad Code - Replace with your actual Ad Unit ID -->
                    <div id="container-1ad3f5e5b0b0a1a1a1a1a1a1a1a1a1a1"></div>
                    <script>
                        var atOptions = {
                            'key' : 'YOUR_ADSTERRA_AD_UNIT_ID',
                            'format' : 'iframe',
                            'height' : 250,
                            'width' : 300,
                            'params' : {}
                        };
                        document.write('<scr' + 'ipt type="text/javascript" src="http' + (location.protocol === 'https:' ? 's' : '') + '://www.profitabledisplaynetwork.com/1ad3f5e5b0b0a1a1a1a1a1a1a1a1a1a1/invoke.js"></scr' + 'ipt>');
                    </script>
                </div>
                
                <div class="control-group">
                    <h3>Upload Image</h3>
                    <input type="file" id="file-input" class="file-input" accept="image/*">
                    <button id="upload-btn" class="btn btn-primary" style="width: 100%;">
                        <i class="fas fa-upload"></i> Select Image
                    </button>
                    <p style="text-align: center; margin: 10px 0; color: var(--gray);">or drag & drop</p>
                </div>
                
                <div class="control-group">
                    <h3>Quick Enhance</h3>
                    <div class="btn-group" style="margin-bottom: 15px;">
                        <button id="auto-enhance-btn" class="btn btn-primary" style="flex-grow: 1;">
                            <i class="fas fa-bolt"></i> Auto Enhance
                        </button>
                    </div>
                    <div class="preset-options">
                        <button class="preset-btn" data-preset="sharpness">Sharpen</button>
                        <button class="preset-btn" data-preset="brightness">Brighten</button>
                        <button class="preset-btn" data-preset="contrast">Contrast</button>
                        <button class="preset-btn" data-preset="denoise">Denoise</button>
                        <button class="preset-btn" data-preset="upscale">Upscale 2x</button>
                        <button class="preset-btn" data-preset="color-correct">Color Correct</button>
                    </div>
                </div>
                
                <!-- Middle Ad Container -->
                <div class="ad-container">
                    <span class="ad-label">Sponsored</span>
                    <!-- Adsterra Native Ad Code - Replace with your actual Native Ad Unit ID -->
                    <div id="container-native-ad"></div>
                    <script>
                        var atOptions = {
                            'key' : 'YOUR_ADSTERRA_NATIVE_AD_UNIT_ID',
                            'format' : 'native',
                            'height' : 300,
                            'width' : 300,
                            'params' : {}
                        };
                        document.write('<scr' + 'ipt type="text/javascript" src="http' + (location.protocol === 'https:' ? 's' : '') + '://www.profitabledisplaynetwork.com/native-ad/invoke.js"></scr' + 'ipt>');
                    </script>
                </div>
                
                <div class="control-group">
                    <h3>Manual Adjustments</h3>
                    <div class="slider-control">
                        <label for="brightness-slider">Brightness</label>
                        <div class="slider-container">
                            <input type="range" min="-100" max="100" value="0" class="slider" id="brightness-slider">
                            <span class="slider-value">0</span>
                        </div>
                    </div>
                    <div class="slider-control">
                        <label for="contrast-slider">Contrast</label>
                        <div class="slider-container">
                            <input type="range" min="-100" max="100" value="0" class="slider" id="contrast-slider">
                            <span class="slider-value">0</span>
                        </div>
                    </div>
                    <div class="slider-control">
                        <label for="saturation-slider">Saturation</label>
                        <div class="slider-container">
                            <input type="range" min="-100" max="100" value="0" class="slider" id="saturation-slider">
                            <span class="slider-value">0</span>
                        </div>
                    </div>
                    <div class="slider-control">
                        <label for="sharpness-slider">Sharpness</label>
                        <div class="slider-container">
                            <input type="range" min="0" max="100" value="0" class="slider" id="sharpness-slider">
                            <span class="slider-value">0</span>
                        </div>
                    </div>
                    <div class="slider-control">
                        <label for="noise-slider">Noise Reduction</label>
                        <div class="slider-container">
                            <input type="range" min="0" max="100" value="0" class="slider" id="noise-slider">
                            <span class="slider-value">0</span>
                        </div>
                    </div>
                    <div class="slider-control">
                        <label for="temperature-slider">Temperature</label>
                        <div class="slider-container">
                            <input type="range" min="-100" max="100" value="0" class="slider" id="temperature-slider">
                            <span class="slider-value">0</span>
                        </div>
                    </div>
                </div>
                
                <div class="control-group">
                    <h3>Export Settings</h3>
                    <div class="format-options">
                        <button class="format-btn active" data-format="jpg">JPG</button>
                        <button class="format-btn" data-format="png">PNG</button>
                        <button class="format-btn" data-format="webp">WEBP</button>
                    </div>
                    <div class="slider-control" style="margin-top: 15px;">
                        <label for="quality-slider">Quality <span id="quality-value">90%</span></label>
                        <div class="slider-container">
                            <input type="range" min="1" max="100" value="90" class="slider" id="quality-slider">
                        </div>
                        <div class="quality-indicator">
                            <span>Smaller file</span>
                            <div class="quality-bar">
                                <div class="quality-progress" id="quality-progress"></div>
                            </div>
                            <span>Better quality</span>
                        </div>
                    </div>
                    <div class="btn-group" style="margin-top: 15px;">
                        <button id="download-btn" class="btn btn-primary" style="flex-grow: 1;">
                            <i class="fas fa-download"></i> Download
                        </button>
                        <button id="save-cloud-btn" class="btn btn-secondary">
                            <i class="fas fa-cloud-upload-alt"></i>
                        </button>
                    </div>
                </div>
                
                <!-- View Counter -->
                <div class="view-counter">
                    <i class="fas fa-eye"></i> <span id="view-count">0</span> users enhancing images now
                </div>
                
                <!-- Bottom Ad Container -->
                <div class="ad-container">
                    <span class="ad-label">Advertisement</span>
                    <!-- Adsterra Popunder Ad Code - Replace with your actual Popunder Ad Unit ID -->
                    <script type="text/javascript">
                        var atOptions = { 
                            'key' : 'YOUR_ADSTERRA_POPUNDER_AD_UNIT_ID',
                            'format' : 'iframe',
                            'height' : 1,
                            'width' : 1,
                            'params' : {}
                        };
                        document.write('<scr' + 'ipt type="text/javascript" src="http' + (location.protocol === 'https:' ? 's' : '') + '://www.profitabledisplaynetwork.com/popunder-ad/invoke.js"></scr' + 'ipt>');
                    </script>
                </div>
                
                <div class="control-group">
                    <h3>Edit History</h3>
                    <div id="history-list">
                        <div class="history-item">
                            <div style="width: 40px; height: 40px; background: #e2e8f0; border-radius: 4px; display: flex; align-items: center; justify-content: center; margin-right: 10px;">
                                <i class="fas fa-image" style="color: #94a3b8;"></i>
                            </div>
                            <div class="history-info">
                                <h4>No history yet</h4>
                                <p>Your edits will appear here</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="editor-container">
                <div class="image-preview">
                    <!-- Sidebar Ad Container -->
                    <div class="ad-container" style="margin-bottom: 20px;">
                        <span class="ad-label">Sponsored Content</span>
                        <!-- Adsterra Banner Ad Code - Replace with your actual Banner Ad Unit ID -->
                        <div id="container-banner-ad"></div>
                        <script>
                            var atOptions = {
                                'key' : 'YOUR_ADSTERRA_BANNER_AD_UNIT_ID',
                                'format' : 'iframe',
                                'height' : 90,
                                'width' : 728,
                                'params' : {}
                            };
                            document.write('<scr' + 'ipt type="text/javascript" src="http' + (location.protocol === 'https:' ? 's' : '') + '://www.profitabledisplaynetwork.com/banner-ad/invoke.js"></scr' + 'ipt>');
                        </script>
                    </div>
                    
                    <div class="preview-area" id="preview-area">
                        <div class="drop-message">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <p>Drag & drop your image here</p>
                            <p>or click to browse files</p>
                        </div>
                        <img id="preview-image" class="preview-image">
                        <div class="loading-overlay" id="loading-overlay">
                            <div class="spinner"></div>
                            <p id="loading-text">Enhancing your image...</p>
                        </div>
                    </div>
                    
                    <div id="compare-container" style="display: none;">
                        <div class="compare-slider">
                            <img id="compare-before" class="compare-before">
                            <img id="compare-after" class="compare-after">
                            <div class="compare-handle"></div>
                        </div>
                        <div class="btn-group" style="justify-content: center; margin-top: 15px;">
                            <button id="compare-btn" class="btn btn-secondary">
                                <i class="fas fa-eye"></i> Toggle Compare
                            </button>
                            <button id="reset-btn" class="btn btn-secondary">
                                <i class="fas fa-undo"></i> Reset
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // DOM Elements
            const fileInput = document.getElementById('file-input');
            const uploadBtn = document.getElementById('upload-btn');
            const previewArea = document.getElementById('preview-area');
            const previewImage = document.getElementById('preview-image');
            const loadingOverlay = document.getElementById('loading-overlay');
            const loadingText = document.getElementById('loading-text');
            const compareContainer = document.getElementById('compare-container');
            const compareBefore = document.getElementById('compare-before');
            const compareAfter = document.getElementById('compare-after');
            const compareBtn = document.getElementById('compare-btn');
            const downloadBtn = document.getElementById('download-btn');
            const saveCloudBtn = document.getElementById('save-cloud-btn');
            const resetBtn = document.getElementById('reset-btn');
            const historyList = document.getElementById('history-list');
            const errorMessage = document.getElementById('error-message');
            const errorText = document.getElementById('error-text');
            const autoEnhanceBtn = document.getElementById('auto-enhance-btn');
            const qualitySlider = document.getElementById('quality-slider');
            const qualityValue = document.getElementById('quality-value');
            const qualityProgress = document.getElementById('quality-progress');
            const viewCount = document.getElementById('view-count');
            
            // State variables
            let originalImage = null;
            let enhancedImage = null;
            let isComparing = false;
            let currentFileName = '';
            
            // Initialize viewer counter
            let viewers = Math.floor(Math.random() * 100) + 50; // Random number between 50-150
            viewCount.textContent = viewers;
            
            // Simulate viewer count changes
            setInterval(() => {
                // Randomly fluctuate the viewer count
                viewers += Math.floor(Math.random() * 5) - 2; // Add -2 to +2
                viewers = Math.max(50, viewers); // Don't go below 50
                viewCount.textContent = viewers;
            }, 30000); // Update every 30 seconds
            
            // Track page views in localStorage
            trackPageView();
            
            function trackPageView() {
                let pageViews = localStorage.getItem('pageViews');
                if (!pageViews) {
                    pageViews = 1;
                } else {
                    pageViews = parseInt(pageViews) + 1;
                }
                localStorage.setItem('pageViews', pageViews);
                
                // You can send this data to your analytics if needed
                console.log('Total page views:', pageViews);
            }
            
            // Initialize quality display
            qualitySlider.addEventListener('input', function() {
                const quality = this.value;
                qualityValue.textContent = `${quality}%`;
                qualityProgress.style.width = `${quality}%`;
            });
            
            // Upload button click
            uploadBtn.addEventListener('click', function() {
                fileInput.click();
            });
            
            // File input change
            fileInput.addEventListener('change', function(e) {
                if (e.target.files.length) {
                    loadImage(e.target.files[0]);
                }
            });
            
            // Drag and drop
            previewArea.addEventListener('dragover', function(e) {
                e.preventDefault();
                previewArea.classList.add('active');
            });
            
            previewArea.addEventListener('dragleave', function() {
                previewArea.classList.remove('active');
            });
            
            previewArea.addEventListener('drop', function(e) {
                e.preventDefault();
                previewArea.classList.remove('active');
                
                if (e.dataTransfer.files.length) {
                    loadImage(e.dataTransfer.files[0]);
                }
            });
            
            // Click to upload
            previewArea.addEventListener('click', function() {
                fileInput.click();
            });
            
            // Slider updates
            document.querySelectorAll('.slider').forEach(slider => {
                slider.addEventListener('input', function() {
                    const valueDisplay = this.nextElementSibling;
                    if (valueDisplay) valueDisplay.textContent = this.value;
                    
                    if (originalImage) {
                        applyEnhancements();
                    }
                });
            });
            
            // Preset buttons
            document.querySelectorAll('.preset-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const preset = this.dataset.preset;
                    applyPreset(preset);
                });
            });
            
            // Format buttons
            document.querySelectorAll('.format-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    document.querySelectorAll('.format-btn').forEach(b => b.classList.remove('active'));
                    this.classList.add('active');
                });
            });
            
            // Auto enhance button
            autoEnhanceBtn.addEventListener('click', function() {
                if (!originalImage) {
                    showError('Please upload an image first');
                    return;
                }
                
                applyPreset('auto');
            });
            
            // Compare button
            compareBtn.addEventListener('click', function() {
                if (!originalImage) {
                    showError('No image to compare');
                    return;
                }
                
                isComparing = !isComparing;
                
                if (isComparing) {
                    previewImage.style.display = 'none';
                    compareContainer.style.display = 'block';
                    this.innerHTML = '<i class="fas fa-eye-slash"></i> Hide Compare';
                } else {
                    previewImage.style.display = 'block';
                    compareContainer.style.display = 'none';
                    this.innerHTML = '<i class="fas fa-eye"></i> Show Compare';
                }
            });
            
            // Download button
            downloadBtn.addEventListener('click', function() {
                if (!enhancedImage) {
                    showError('Please enhance an image first');
                    return;
                }
                
                downloadImage();
            });
            
            // Save to cloud button
            saveCloudBtn.addEventListener('click', function() {
                if (!enhancedImage) {
                    showError('Please enhance an image first');
                    return;
                }
                
                // In a real app, this would save to cloud storage
                showLoading('Saving to cloud...');
                setTimeout(() => {
                    hideLoading();
                    alert('Image saved to cloud storage (simulated)');
                }, 1500);
            });
            
            // Reset button
            resetBtn.addEventListener('click', function() {
                if (!originalImage) {
                    showError('No image to reset');
                    return;
                }
                
                resetSliders();
                applyEnhancements(true); // Reset to original
            });
            
            // Compare slider functionality
            const compareSlider = document.querySelector('.compare-slider');
            const compareHandle = document.querySelector('.compare-handle');
            
            let isDragging = false;
            
            compareHandle.addEventListener('mousedown', function() {
                isDragging = true;
            });
            
            document.addEventListener('mousemove', function(e) {
                if (!isDragging) return;
                
                const rect = compareSlider.getBoundingClientRect();
                let x = e.clientX - rect.left;
                
                // Keep within bounds
                x = Math.max(0, Math.min(x, rect.width));
                
                const percent = (x / rect.width) * 100;
                
                compareBefore.style.clipPath = `inset(0 ${100 - percent}% 0 0)`;
                compareAfter.style.clipPath = `inset(0 0 0 ${percent}%)`;
                compareHandle.style.left = `${percent}%`;
            });
            
            document.addEventListener('mouseup', function() {
                isDragging = false;
            });
            
            // Touch support for compare slider
            compareHandle.addEventListener('touchstart', function() {
                isDragging = true;
            });
            
            document.addEventListener('touchmove', function(e) {
                if (!isDragging) return;
                
                const touch = e.touches[0];
                const rect = compareSlider.getBoundingClientRect();
                let x = touch.clientX - rect.left;
                
                // Keep within bounds
                x = Math.max(0, Math.min(x, rect.width));
                
                const percent = (x / rect.width) * 100;
                
                compareBefore.style.clipPath = `inset(0 ${100 - percent}% 0 0)`;
                compareAfter.style.clipPath = `inset(0 0 0 ${percent}%)`;
                compareHandle.style.left = `${percent}%`;
            });
            
            document.addEventListener('touchend', function() {
                isDragging = false;
            });
            
            // Helper functions
            function loadImage(file) {
                if (!file.type.match('image.*')) {
                    showError('Please select an image file (JPEG, PNG, etc.)');
                    return;
                }
                
                currentFileName = file.name.split('.')[0];
                
                const reader = new FileReader();
                
                reader.onload = function(e) {
                    originalImage = e.target.result;
                    
                    previewImage.onload = function() {
                        hideError();
                        previewImage.style.display = 'block';
                        
                        compareBefore.src = originalImage;
                        compareAfter.src = originalImage;
                        
                        // Show compare controls
                        compareContainer.style.display = 'block';
                        isComparing = false;
                        compareBtn.innerHTML = '<i class="fas fa-eye"></i> Show Compare';
                        
                        // Add to history
                        addToHistory('Original', originalImage);
                        
                        // Auto-enhance by default
                        setTimeout(() => {
                            applyPreset('auto');
                        }, 500);
                    };
                    
                    previewImage.onerror = function() {
                        showError('Error loading image. Please try another file.');
                    };
                    
                    previewImage.src = originalImage;
                };
                
                reader.onerror = function() {
                    showError('Error reading file. Please try again.');
                };
                
                showLoading('Loading image...');
                reader.readAsDataURL(file);
            }
            
            function applyEnhancements(reset = false) {
                if (!originalImage) return;
                
                showLoading('Applying enhancements...');
                
                // Simulate processing delay
                setTimeout(() => {
                    // In a real app, this would apply actual image enhancements
                    // For demo, we'll just use the same image but simulate enhancement
                    enhancedImage = reset ? originalImage : simulateEnhancementEffect(originalImage);
                    
                    previewImage.src = enhancedImage;
                    compareAfter.src = enhancedImage;
                    
                    hideLoading();
                    
                    // Add to history if not reset
                    if (!reset) {
                        addToHistory('Enhanced', enhancedImage);
                    }
                }, 1000);
            }
            
            function simulateEnhancementEffect(imageSrc) {
                // In a real app, this would use actual image processing
                // For demo, we'll return the same image but could apply some canvas filters
                return imageSrc;
            }
            
            function applyPreset(preset) {
                // Reset all sliders first
                resetSliders();
                
                // Apply preset values
                switch(preset) {
                    case 'auto':
                        document.getElementById('brightness-slider').value = '15';
                        document.getElementById('contrast-slider').value = '20';
                        document.getElementById('saturation-slider').value = '10';
                        document.getElementById('sharpness-slider').value = '25';
                        document.getElementById('noise-slider').value = '30';
                        document.getElementById('temperature-slider').value = '5';
                        break;
                    case 'sharpness':
                        document.getElementById('sharpness-slider').value = '50';
                        break;
                    case 'brightness':
                        document.getElementById('brightness-slider').value = '30';
                        break;
                    case 'contrast':
                        document.getElementById('contrast-slider').value = '40';
                        break;
                    case 'denoise':
                        document.getElementById('noise-slider').value = '70';
                        break;
                    case 'upscale':
                        showLoading('Upscaling image...');
                        setTimeout(() => {
                            alert('In a real app, this would upscale your image 2x using AI algorithms');
                            hideLoading();
                        }, 1500);
                        return;
                    case 'color-correct':
                        document.getElementById('temperature-slider').value = '10';
                        document.getElementById('saturation-slider').value = '15';
                        break;
                }
                
                // Update display values
                document.querySelectorAll('.slider').forEach(slider => {
                    const valueDisplay = slider.nextElementSibling;
                    if (valueDisplay) valueDisplay.textContent = slider.value;
                });
                
                applyEnhancements();
            }
            
            function addToHistory(label, imageSrc) {
                // Clear placeholder if exists
                if (historyList.firstChild && historyList.firstChild.querySelector('.fa-image')) {
                    historyList.innerHTML = '';
                }
                
                const historyItem = document.createElement('div');
                historyItem.className = 'history-item';
                
                const thumbSrc = imageSrc;
                
                historyItem.innerHTML = `
                    <img src="${thumbSrc}" class="history-thumb">
                    <div class="history-info">
                        <h4>${label}</h4>
                        <p>${new Date().toLocaleTimeString()}</p>
                    </div>
                `;
                
                historyItem.addEventListener('click', function() {
                    if (label === 'Original') {
                        previewImage.src = originalImage;
                        compareAfter.src = originalImage;
                    } else {
                        previewImage.src = enhancedImage;
                        compareAfter.src = enhancedImage;
                    }
                });
                
                historyList.insertBefore(historyItem, historyList.firstChild);
                
                // Limit history to 10 items
                if (historyList.children.length > 10) {
                    historyList.removeChild(historyList.lastChild);
                }
            }
            
            function downloadImage() {
                if (!enhancedImage) return;
                
                showLoading('Preparing download...');
                
                // In a real app, this would create an actual downloadable file
                // For demo, we'll simulate the download
                setTimeout(() => {
                    hideLoading();
                    
                    const format = document.querySelector('.format-btn.active').dataset.format;
                    const quality = qualitySlider.value;
                    
                    // Create a temporary link
                    const link = document.createElement('a');
                    link.href = enhancedImage;
                    link.download = `${currentFileName}_enhanced.${format}`;
                    document.body.appendChild(link);
                    link.click();
                    document.body.removeChild(link);
                    
                    // Add to history
                    addToHistory(`Downloaded (${format})`, enhancedImage);
                }, 800);
            }
            
            function resetSliders() {
                document.querySelectorAll('.slider').forEach(slider => {
                    // Reset to 0 except quality which stays at 90
                    if (slider.id !== 'quality-slider') {
                        slider.value = slider.id.includes('noise') || slider.id.includes('sharpness') ? '0' : '0';
                        const valueDisplay = slider.nextElementSibling;
                        if (valueDisplay) valueDisplay.textContent = slider.value;
                    }
                });
            }
            
            function showLoading(text) {
                loadingText.textContent = text;
                loadingOverlay.style.display = 'flex';
            }
            
            function hideLoading() {
                loadingOverlay.style.display = 'none';
            }
            
            function showError(message) {
                errorText.textContent = message;
                errorMessage.style.display = 'flex';
            }
            
            function hideError() {
                errorMessage.style.display = 'none';
            }
        });
    </script>
</body>
</html>

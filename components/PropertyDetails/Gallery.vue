<template>
    <div class="mt-28 bg-white">
        <!-- Header -->
        <!-- <header class="bg-white shadow-sm border-b">
            <div class="container mx-auto px-4 py-4">
                <div class="flex items-center justify-between">
                    <div class="flex items-center space-x-2">
                        <Icon name="mdi:map-marker" class="text-gray-600" />
                        <span class="text-gray-700">Gatlinburg, Tennessee, United States</span>
                    </div>
                    <button
                        class="flex items-center space-x-2 bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition-colors">
                        <Icon name="mdi:share-variant" />
                        <span>Share</span>
                    </button>
                </div>
            </div>
        </header> -->

        <!-- Main Gallery Section -->
        <div class="container mx-auto px-4 py-6">
            <!-- Image Grid -->
            <div class="grid grid-cols-2 md:grid-cols-4 gap-2 rounded-2xl" id="imageGrid">
                <!-- Main large image -->
                <div class="col-span-2 row-span-2 relative cursor-pointer group" @click="openLightbox(0)">
                    <img src="/Gallery/676cfd0cb6ecd.avif" alt="Cabin Exterior" class="w-full object-fit">
                </div>

                <!-- Secondary images -->
                <div class="relative cursor-pointer group" @click="openLightbox(1)">
                    <img src="/Gallery/676cfd0cb6ecd.avif" alt="Cabin Side View" class="w-full object-fit">
                </div>

                <div class="relative cursor-pointer group" @click="openLightbox(2)">
                    <img src="/Gallery/676cfd0cb6ecd.avif" alt="Deck View" class="w-full object-fit">
                </div>

                <div class="relative cursor-pointer group" @click="openLightbox(3)">
                    <img src="/Gallery/676cfd0cb6ecd.avif" alt="King Bedroom" class="w-full object-fit">
                </div>

                <div class="relative cursor-pointer group" @click="openLightbox(4)">
                    <img src="/Gallery/676cfd0cb6ecd.avif" alt="Game Room" class="w-full object-fit">
                </div>
            </div>

            <!-- Show All Button -->
            <div class="mt-4 flex justify-end -translate-y-32 -translate-x-3">
                <button @click="openLightbox(4)" title="Show all photos"
                    class="flex items-center space-x-2 bg-gray-500 text-white border-gray-300 px-8K py-2 hover:bg-gray-600 transition-colors shadow-sm">
                    <span class="font-medium">Show All</span>
                </button>
            </div>
        </div>

        <!-- Lightbox Modal -->
        <div id="lightboxModal" class="fixed inset-0 bg-black opacity-95 z-40 hidden">
            <!-- Progress Bar for Slideshow -->
            <div id="progressBar" class="absolute top-0 left-0 h-1 bg-blue-600 progress-bar z-10 hidden"
                style="width: 0%"></div>

            <!-- Top Controls -->
            <div class="absolute top-0 left-0 right-0 z-30 image-overlay">
                <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between">
                    <div class="flex items-center space-x-4">

                        <span class="text-white text-lg font-medium" id="imageCounter" aria-live="polite">1 / 12</span>
                    </div>
                    <div class="flex items-center space-x-4 border border-gray-800 bg-gray-500 p-2">
                        <button @click="startSlideshow()" id="slideshowBtn" aria-label="Start slideshow"
                            title="Start slideshow" class="flex items-center text-white cursor-pointer textContent">
                            <Icon name="lucide:play" id="slideshowIcon" />
                        </button>
                        <button @click="toggleThumbnails()" aria-label="Show thumbnails" title="Show thumbnails"
                            class="text-white cursor-pointer textContent">
                            <Icon name="lucide:grid-3x3" class="text-lg" />
                        </button>
                        <button @click="searchImages()" aria-label="Search images" title="Search images"
                            class="text-white cursor-pointer">
                            <Icon name="mdi:search" class="text-lg" />
                        </button>
                        <button @click="toggleFullscreen()" aria-label="Toggle fullscreen" title="Toggle fullscreen"
                            class="text-white cursor-pointer">
                            <Icon name="lucide:fullscreen" class="text-lg" id="fullscreenIcon" />
                        </button>
                        <button @click="openShareModal()" aria-label="Share image" title="Share image"
                            class="text-white cursor-pointer">
                            <Icon name="lucide:share-2" class="text-lg" />
                        </button>
                        <button @click="closeLightbox()" aria-label="Close lightbox" title="Close lightbox"
                            class="text-white cursor-pointer">
                            <Icon name="lucide:x" class="text-lg" />
                        </button>
                    </div>
                </div>
            </div>

            <!-- Main Image Container -->
            <div class="flex items-center justify-center h-full px-16">
                <button @click="previousImage()" aria-label="Previous image" title="Previous image"
                    class="absolute left-6 text-white cursor-pointer  z-20">
                    <Icon name="mdi:chevron-left" class="text-2xl" />
                </button>

                <div class="max-w-5xl max-h-full flex items-center justify-center">
                    <img id="lightboxImage" src="" alt="" class="max-w-full max-h-full object-contain slideshow-active">
                </div>

                <button @click="nextImage()" aria-label="Next image" title="Next image"
                    class="absolute right-6 text-white cursor-pointer z-20">
                    <Icon name="mdi:chevron-right" class="text-2xl" />
                </button>
            </div>

            <!-- Thumbnail Panel -->
            <div id="thumbnailPanel"
                class="absolute right-0 top-3 h-full bg-black bg-opacity-90 w-80 transform translate-x-full transition-transform duration-300 z-20 overflow-y-auto">
                <div class="p-4">
                    <div class="flex items-center justify-between mb-4">
                        <button @click="toggleThumbnails()" class="text-white hover:text-gray-300">
                            <Icon name="mdi:x" class="text-xl" />
                        </button>
                    </div>
                    <div class="grid grid-cols-2 gap-2" id="thumbnailGrid">
                        <!-- Thumbnails will be populated by JavaScript -->
                    </div>
                </div>
            </div>
        </div>

        <!-- Share Modal -->
        <div id="shareModal" class="fixed inset-0 bg-black opacity-90 z-50 hidden">
            <div class="bg-white rounded-lg p-6 max-w-md w-full mx-4">
                <div class="flex items-center justify-between mb-4">
                    <h3 class="text-xl font-semibold">Share</h3>
                    <button id="copied" class="">
                        <span class="sr-only">copied</span>
                    </button>
                    <button @click="closeShareModal()" class="text-gray-500 hover:text-gray-700">
                        <Icon name="mdi:close" class="text-xl" />
                    </button>
                </div>

                <div class="flex space-x-3 mb-4">
                    <button @click="shareToFacebook()"
                        class="flex-1 bg-blue-600 text-white py-3 px-4 rounded-lg hover:bg-blue-700 transition-colors flex items-center justify-center space-x-2">
                        <Icon name="mdi:facebook" class="text-xl" />
                        <span>Facebook</span>
                    </button>
                    <button @click="shareToTwitter()"
                        class="flex-1 bg-blue-400 text-white py-3 px-4 rounded-lg hover:bg-blue-500 transition-colors flex items-center justify-center space-x-2">
                        <Icon name="mdi:twitter" class="text-xl" />
                        <span>Twitter</span>
                    </button>
                    <button @click="shareToPinterest()"
                        class="flex-1 bg-red-600 text-white py-3 px-4 rounded-lg hover:bg-red-700 transition-colors flex items-center justify-center space-x-2">
                        <Icon name="mdi:pinterest" class="text-xl" />
                        <span>Pinterest</span>
                    </button>
                </div>

                <div class="border-t pt-4">
                    <input type="text" value="https://www.relaxresetbookdirect.com/cabin-w-fire-pit-and-mtn-views"
                        class="w-full px-3 py-2 border border-gray-300 rounded-lg bg-gray-50" readonly>
                    <button @click="copyLink()"
                        class="w-full mt-2 bg-gray-800 text-white py-2 px-4 rounded-lg hover:bg-gray-900 transition-colors">
                        Copy Link
                    </button>
                </div>
            </div>
        </div>

        <!-- Show All Images Modal -->
        <div id="showAllModal" class="fixed inset-0 bg-black bg-opacity-95 z-40 hidden overflow-y-auto">
            <div class="min-h-screen p-6">
                <div class="flex items-center justify-between mb-6">
                    <h2 class="text-white text-2xl font-semibold">All Photos - Cabin w/ Fire Pit and Mtn Views</h2>
                    <button @click="closeShowAll()"
                        class="text-white bg-black bg-opacity-50 px-4 py-2 rounded-lg hover:bg-opacity-70 transition-colors">
                        <Icon name="mdi:x" class="text-lg" />
                    </button>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4" id="allImagesGrid">
                    <!-- All images will be populated by JavaScript -->
                </div>
            </div>
        </div>
    </div>
</template>
<script setup>
const images = [
    { src: '/Gallery/676cfd0cb6ecd.avif', alt: 'Cabin Exterior' },
    { src: '/Gallery/676d23a4bc7b9.webp', alt: 'Cabin Side View' },
    { src: '/Gallery/676d23a4bd3d4.webp', alt: 'Deck View' },
    { src: '/Gallery/676d23a4bdb88.webp', alt: 'King Bedroom' },
    { src: '/Gallery/676d23a4beb53.webp', alt: 'Game Room with Pool Table' },
    { src: '/Gallery/676d23a4c1d88.webp', alt: 'Living Room' },
    { src: '/Gallery/676d23a4c133b.webp', alt: 'Kitchen' },
    { src: '/Gallery/676d23a4c261b.webp', alt: 'Bathroom' },
    { src: '/Gallery/676d23b594b80.webp', alt: 'Hot Tub Area' },
    { src: '/Gallery/676d23b595a40.webp', alt: 'Mountain View' },
    { src: '/Gallery/676d23b5928ba.webp', alt: 'Forest Setting' },
    { src: '/Gallery/676d23b5930e6.webp', alt: 'Fire Pit Area' },
    { src: '/Gallery/676d23b5938bb.webp', alt: 'Deck View' },
    { src: '/Gallery/676d23b5952e0.webp', alt: 'Cabin Side View' },
    { src: '/Gallery/676d23b59441d.webp', alt: 'King Bedroom' },
    { src: '/Gallery/676d23b590965.webp', alt: 'Game Room with Pool Table' },
    { src: '/Gallery/676d23b591692.webp', alt: 'Cabin Exterior' },
    { src: '/Gallery/676d23b592029.webp', alt: 'Living Room' },
    { src: '/Gallery/676d23c4d4f30.webp', alt: 'Kitchen' },
    { src: '/Gallery/676d23c4d69b1.webp', alt: 'Bathroom' },
    { src: '/Gallery/676d23c4d6291.webp', alt: 'Hot Tub Area' },
    { src: '/Gallery/676d23831c5fc.webp', alt: 'Mountain View' },
    { src: '/Gallery/676d23831d334.webp', alt: 'Forest Setting' },
    { src: '/Gallery/676d23831ee7a.webp', alt: 'Fire Pit Area' },
    { src: '/Gallery/676d23955beff.webp', alt: 'Fire Pit Area' },
    { src: '/Gallery/676d239557e54.webp', alt: 'Fire Pit Area' }
];

let currentImageIndex = 0;
let isSlideshow = false;
let slideshowInterval;
let isFullscreen = false;
let thumbnailsVisible = false;

function openLightbox(index) {
    currentImageIndex = index;
    document.getElementById('lightboxModal').classList.remove('hidden');
    document.body.style.overflow = 'hidden';
    updateLightboxImage();
    populateThumbnails();
}

function closeLightbox() {
    document.getElementById('lightboxModal').classList.add('hidden');
    document.body.style.overflow = 'auto';
    stopSlideshow();
    exitFullscreen();
}

function updateLightboxImage() {
    const lightboxImage = document.getElementById('lightboxImage');
    lightboxImage.src = images[currentImageIndex].src;
    lightboxImage.alt = images[currentImageIndex].alt;
    document.getElementById('imageCounter').textContent = `${currentImageIndex + 1} / ${images.length}`;

    // Update active thumbnail
    updateActiveThumbnail();
}

function nextImage() {
    const lightboxImage = document.getElementById('lightboxImage');
    // Remove the current class to reset animation
    lightboxImage.classList.remove('slideshow-active');
    // Force reflow
    void lightboxImage.offsetWidth;

    currentImageIndex = (currentImageIndex + 1) % images.length;
    updateLightboxImage();

    // Add animation class
    lightboxImage.classList.add('slideshow-active');
}

function previousImage() {
    const lightboxImage = document.getElementById('lightboxImage');
    // Remove the current class to reset animation
    lightboxImage.classList.remove('slideshow-active');
    // Force reflow
    void lightboxImage.offsetWidth;

    currentImageIndex = (currentImageIndex - 1 + images.length) % images.length;
    updateLightboxImage();

    // Add animation class
    lightboxImage.classList.add('slideshow-active');
}

function startSlideshow() {
    if (!isSlideshow) {
        isSlideshow = true;
        document.getElementById('slideshowIcon').setAttribute('name', 'lucide:pause');
       
        document.getElementById('progressBar').classList.remove('hidden');

        let progress = 0;
        const progressBar = document.getElementById('progressBar');
        const slideDuration = 3000; // 3 seconds per slide
        const updateInterval = 20; // Update every 20ms for smoother animation
        const increment = (updateInterval / slideDuration) * 100;

        slideshowInterval = setInterval(() => {
            progress += increment;
            progressBar.style.width = `${progress}%`;

            if (progress >= 100) {
                progress = 0;
                progressBar.style.width = '0%';
                // Add fadeOut class to current image
                const lightboxImage = document.getElementById('lightboxImage');
                lightboxImage.classList.add('slideshow-active');
                nextImage();
                // Remove fadeOut class after animation completes
                setTimeout(() => {
                    lightboxImage.classList.remove('slideshow-active');
                }, 500);
            }
        }, updateInterval);
    } else {
        stopSlideshow();
    }
}

function stopSlideshow() {
    isSlideshow = false;
    clearInterval(slideshowInterval);
    document.getElementById('slideshowIcon').setAttribute('name', 'lucide:play');
    document.getElementById('progressBar').classList.add('hidden');
    document.getElementById('progressBar').style.width = '0%';
}

function toggleFullscreen() {
    if (!isFullscreen) {
        if (document.documentElement.requestFullscreen) {
            document.documentElement.requestFullscreen();
        }
        document.getElementById('fullscreenIcon').setAttribute('name', 'lucide:minimize');
        isFullscreen = true;
    } else {
        if (document.exitFullscreen) {
            document.exitFullscreen();
        }
        document.getElementById('fullscreenIcon').setAttribute('name', 'lucide:fullscreen');
        isFullscreen = false;
    }
}

function exitFullscreen() {
    if (isFullscreen && document.exitFullscreen) {
        document.exitFullscreen();
        document.getElementById('fullscreenIcon').setAttribute('name', 'lucide:fullscreen');
        isFullscreen = false;
    }
}

function toggleThumbnails() {
    const panel = document.getElementById('thumbnailPanel');
    if (!thumbnailsVisible) {
        panel.classList.remove('translate-x-full');
        thumbnailsVisible = true;
    } else {
        panel.classList.add('translate-x-full');
        thumbnailsVisible = false;
    }
}

function populateThumbnails() {
    const thumbnailGrid = document.getElementById('thumbnailGrid');
    thumbnailGrid.innerHTML = '';

    images.forEach((image, index) => {
        const thumbnailDiv = document.createElement('div');
        thumbnailDiv.className = 'relative cursor-pointer thumbnail-hover';
        thumbnailDiv.onclick = () => selectThumbnail(index);
        thumbnailDiv.innerHTML = `
                    <img src="${image.src}" alt="${image.alt}" class="w-full h-24 object-cover rounded-lg ${index === currentImageIndex ? 'ring-2 ring-blue-500' : ''}">
                    ${index === currentImageIndex ? '<div class="absolute inset-0 bg-opacity-20 rounded-lg"></div>' : ''}
                `;
        thumbnailGrid.appendChild(thumbnailDiv);
    });
}

function selectThumbnail(index) {
    currentImageIndex = index;
    updateLightboxImage();
}

function updateActiveThumbnail() {
    const thumbnails = document.querySelectorAll('#thumbnailGrid > div');
    thumbnails.forEach((thumb, index) => {
        const img = thumb.querySelector('img');
        const overlay = thumb.querySelector('div');
        if (index === currentImageIndex) {
            img.classList.add('ring-2', 'ring-blue-500');
            if (!overlay) {
                thumb.innerHTML += '<div class="absolute inset-0 bg-opacity-20 rounded-lg"></div>';
            }
        } else {
            img.classList.remove('ring-2', 'ring-blue-500');
            if (overlay) {
                overlay.remove();
            }
        }
    });
}

function openShareModal() {
    const modal = document.getElementById('shareModal');
    modal.classList.remove('hidden');
    modal.classList.add('flex', 'items-center', 'justify-center');
}

function closeShareModal() {
    const modal = document.getElementById('shareModal');
    modal.classList.add('hidden');
    modal.classList.remove('flex', 'items-center', 'justify-center');
}

function shareToFacebook() {
    const url = encodeURIComponent('https://www.relaxresetbookdirect.com/cabin-w-fire-pit-and-mtn-views');
    window.open(`https://www.facebook.com/sharer/sharer.php?u=${url}`, '_blank', 'width=600,height=400');
}

function shareToTwitter() {
    const url = encodeURIComponent('https://www.relaxresetbookdirect.com/cabin-w-fire-pit-and-mtn-views');
    const text = encodeURIComponent('Check out this amazing cabin with fire pit and mountain views!');
    window.open(`https://twitter.com/intent/tweet?url=${url}&text=${text}`, '_blank', 'width=600,height=400');
}

function shareToPinterest() {
    const url = encodeURIComponent('https://www.relaxresetbookdirect.com/cabin-w-fire-pit-and-mtn-views');
    const description = encodeURIComponent('Amazing cabin with fire pit and mountain views');
    const media = encodeURIComponent(images[currentImageIndex].src);
    window.open(`https://pinterest.com/pin/create/button/?url=${url}&description=${description}&media=${media}`, '_blank', 'width=600,height=400');
}

async function copyLink() {
    const input = document.querySelector('#shareModal input');
    const text = input.value;

    try {
        // Use modern Clipboard API if available
        if (navigator.clipboard && navigator.clipboard.writeText) {
            await navigator.clipboard.writeText(text);
        } else {
            // Fallback to older method
            input.select();
            document.execCommand('copy');
        }

        const button = document.getElementById('copied');
        console.log('Link copied to clipboard:', button,document.querySelector('#shareModal button:last-child'));
        // const originalText = button.textContent;
        button.textContent = 'Copied!';
        button.classList.add('bg-green-600', 'hover:bg-green-700', 'text-white', 'px-4', 'py-2', 'rounded-lg');
        button.classList.remove('bg-gray-800', 'hover:bg-gray-900');

        setTimeout(() => {
            button.textContent = '';
            button.classList.remove('bg-green-600', 'hover:bg-green-700');
        }, 2000);
    } catch (err) {
        console.error('Failed to copy: ', err);
        alert('Failed to copy link. Please try selecting and copying manually.');
    }
}

function searchImages() {
    alert('Search functionality would be implemented here!');
}


function closeShowAll() {
    document.getElementById('showAllModal').classList.add('hidden');
    document.body.style.overflow = 'auto';
}

// Event handlers will be set up after component is mounted
onMounted(() => {
    // Keyboard navigation
    window.addEventListener('keydown', handleKeyDown);

    // Handle fullscreen change
    document.addEventListener('fullscreenchange', handleFullscreenChange);
});

// Clean up event listeners when component is unmounted
onBeforeUnmount(() => {
    window.removeEventListener('keydown', handleKeyDown);
    document.removeEventListener('fullscreenchange', handleFullscreenChange);
});

// Keyboard navigation handler
function handleKeyDown(e) {
    if (document.getElementById('lightboxModal').classList.contains('hidden')) return;

    switch (e.key) {
        case 'ArrowLeft':
            previousImage();
            break;
        case 'ArrowRight':
        case ' ':
            e.preventDefault();
            nextImage();
            break;
        case 'Escape':
            closeLightbox();
            break;
        case 'f':
        case 'F':
            toggleFullscreen();
            break;
    }
}

// Fullscreen change handler
function handleFullscreenChange() {
    isFullscreen = !!document.fullscreenElement;
    document.getElementById('fullscreenIcon').setAttribute('name', isFullscreen ? 'mdi:fullscreen-exit' : 'mdi:fullscreen');
}
</script>

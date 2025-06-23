<template>
    <!-- Newsletter Modal Button (Only shown in demo mode) -->
    <div v-if="demoMode" class="text-center">
        <h1 class="text-3xl font-bold text-gray-800 mb-4">Welcome to Our Website</h1>
        <p class="text-gray-600 mb-6">This is a demo page. The modal will appear automatically for first-time visitors.
        </p>
        <button @click="showModal"
            class="bg-orange-600 text-white px-6 py-3 rounded-lg hover:bg-orange-700 transition-colors">
            Show Modal Again
        </button>
    </div>

    <!-- Modal Overlay -->
    <div v-show="isModalVisible" class="fixed inset-0 modal-overlay flex items-center justify-center z-50 fade-in">
        <!-- Modal Container -->
        <div class="bg-white shadow-2xl overflow-hidden max-w-4xl w-full mx-4 modal-enter">
            <div class="flex flex-col lg:flex-row">

                <!-- Left Side - Image -->
                <div
                    class="lg:w-1/2 bg-gradient-to-br from-gray-100 to-gray-200 p-8 flex items-center justify-center min-h-[300px] lg:min-h-[500px]">
                    <div class="relative">
                        <!-- Fashion models illustration -->
                        <div class="flex items-end space-x-2">
                            <!-- Person 1 -->
                            <div class="w-16 h-20 bg-orange-400 rounded-t-full relative">
                                <div class="w-4 h-4 bg-orange-300 rounded-full absolute top-2 left-6"></div>
                                <div class="w-12 h-6 bg-green-600 absolute bottom-0 left-2 rounded-t-lg"></div>
                            </div>
                            <!-- Person 2 -->
                            <div class="w-18 h-24 bg-gray-700 rounded-t-full relative">
                                <div class="w-4 h-4 bg-orange-300 rounded-full absolute top-2 left-7"></div>
                                <div class="w-14 h-8 bg-gray-800 absolute bottom-0 left-2 rounded-t-lg"></div>
                            </div>
                            <!-- Person 3 -->
                            <div class="w-15 h-22 bg-green-400 rounded-t-full relative">
                                <div class="w-4 h-4 bg-orange-300 rounded-full absolute top-2 left-5"></div>
                                <div class="w-11 h-7 bg-gray-600 absolute bottom-0 left-2 rounded-t-lg"></div>
                            </div>
                            <!-- Person 4 -->
                            <div class="w-17 h-26 bg-orange-300 rounded-t-full relative">
                                <div class="w-4 h-4 bg-orange-400 rounded-full absolute top-2 left-6"></div>
                                <div class="w-13 h-9 bg-gray-800 absolute bottom-0 left-2 rounded-t-lg"></div>
                            </div>
                        </div>
                        <!-- Ground -->
                        <div class="w-full h-3 bg-gray-300 mt-1 rounded"></div>
                        <!-- Plants -->
                        <div class="absolute -right-4 -top-8">
                            <div class="w-8 h-16 bg-green-500 rounded-full opacity-70"></div>
                            <div class="w-6 h-12 bg-green-400 rounded-full opacity-70 absolute -right-2 top-2"></div>
                        </div>
                    </div>
                </div>

                <!-- Right Side - Form -->
                <div class="lg:w-1/2 bg-[#004369] text-white p-8 lg:p-12 relative">

                    <!-- Close Button -->
                    <button @click="closeModal"
                        class="absolute top-4 right-4 w-8 h-8 border-2 bg-[#004369] bg-opacity-20 rounded-full flex items-center justify-center hover:bg-opacity-30 transition-all">
                        <Icon name="lucide:x" class="text-gray-200 text-lg" />
                    </button>

                    <!-- Content -->
                    <div class="max-w-sm">
                        <h2 class="text-2xl lg:text-3xl text-center font-bold mb-6 leading-tight">
                            SUBSCRIBE TO OUR<br>
                            <span class="text-white">NEWSLETTER</span>
                        </h2>

                        <!-- Benefits List -->
                        <div class="space-y-3 mb-4">
                            <div class="flex items-center space-x-3">
                                <Icon name="lucide:circle-check-big" class="text-white text-lg flex-shrink-0" />
                                <span class="text-sm">Receive personalised communities and promotions</span>
                            </div>
                            <div class="flex items-center space-x-3">
                                <Icon name="lucide:circle-check-big" class="text-white text-lg flex-shrink-0" />
                                <span class="text-sm">Discover new products and promotions</span>
                            </div>
                            <div class="flex items-center space-x-3">
                                <Icon name="lucide:circle-check-big" class="text-white text-lg flex-shrink-0" />
                                <span class="text-sm">Receive updates on our sustainability mission</span>
                            </div>
                        </div>

                        <!-- Email Input -->
                        <div class="mb-4">
                            <input v-model="email" type="email" placeholder="Email address"
                                class="w-full px-4 py-1 bg-gray-200 border border-gray-200 text-gray-800 placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-white focus:ring-opacity-50"
                                required>
                        </div>

                        <!-- Checkbox -->
                        <div class="flex items-start space-x-2 mb-6">
                            <input v-model="consent" type="checkbox" id="consent" class=" mt-0.5"
                                required>
                            <label for="consent" class="text-xs leading-relaxed cursor-pointer">
                                You consent to the processing of your personal data for marketing and profiling
                                purposes as described in our
                                <a href="#" class="underline hover:no-underline">Privacy Policy</a>
                            </label>
                        </div>

                        <!-- Submit Button -->
                         <div class="flex justify-center">

                             <button @click="handleSubmit"
                             class=" bg-[#1B7895] textColor py-2 px-6 font-semibold hover:bg-gray-100 transition-colors focus:outline-none focus:ring-2 focus:ring-white focus:ring-opacity-50">
                             SIGN ME UP
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

// Props
const props = defineProps({
    demoMode: {
        type: Boolean,
        default: false
    }
});

// Reactive state
const isModalVisible = ref(false);
const email = ref('');
const consent = ref(false);
let hasVisited = ref(false);

// Show/hide modal functions
const showModal = () => {
    isModalVisible.value = true;
    document.body.style.overflow = 'hidden';
};

const closeModal = () => {
    isModalVisible.value = false;
    document.body.style.overflow = 'auto';
    // Mark as visited
    if (process.client) {
        localStorage.setItem('hasVisited', 'true');
    }
};

// Handle form submission
const handleSubmit = () => {
    if (!email.value) {
        alert('Please enter your email address');
        return;
    }

    if (!consent.value) {
        alert('Please accept the privacy policy');
        return;
    }

    // Here you would typically send the data to your server
    alert('Thank you for subscribing! (This is a demo)');
    closeModal();
};

// Lifecycle hooks
onMounted(() => {
    // Check if user has visited before
    if (process.client) {
        hasVisited.value = localStorage.getItem('hasVisited') === 'true';
    }

    // Show modal for first-time visitors after a delay
    if (!hasVisited.value) {
        setTimeout(showModal, 1000);
    }

    // Event listeners
    // Close modal when clicking outside
    const handleOutsideClick = (e) => {
        const modalOverlay = document.querySelector('.modal-overlay');
        if (modalOverlay && e.target === modalOverlay) {
            closeModal();
        }
    };

    // Close modal with Escape key
    const handleEscapeKey = (e) => {
        if (e.key === 'Escape') {
            closeModal();
        }
    };

    document.addEventListener('click', handleOutsideClick);
    document.addEventListener('keydown', handleEscapeKey);

    // Cleanup function
    onUnmounted(() => {
        document.removeEventListener('click', handleOutsideClick);
        document.removeEventListener('keydown', handleEscapeKey);
    });
});
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

.modal-overlay {
    backdrop-filter: blur(8px);
    background: rgba(0, 0, 0, 0.6);
}

.modal-enter {
    animation: modalEnter 0.3s ease-out;
}

@keyframes modalEnter {
    from {
        opacity: 0;
        transform: scale(0.9);
    }

    to {
        opacity: 1;
        transform: scale(1);
    }
}

.fade-in {
    animation: fadeIn 0.3s ease-out;
}

@keyframes fadeIn {
    from {
        opacity: 0;
    }

    to {
        opacity: 1;
    }
}
</style>
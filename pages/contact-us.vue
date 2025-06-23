<template>
    <!-- <HomeBanner /> -->
    <div class="relative h-[45rem] overflow-hidden">
        <div class="flex h-full slide" style="width: 500%;">
            <!-- Slide 1 -->
            <div class="w-1/5 h-full bg-cover bg-center relative"
                style="background-image: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)), url('/contact-us-banner.jpg');">
                <div class="absolute inset-0 flex items-center justify-center text-center text-white px-4">
                    <div>
                        <h1 class="text-4xl md:text-6xl font-bold mb-4">Contact Us</h1>
                        <p class="text-lg md:text-xl mb-8 max-w-3xl">Your Ultimate Inlet Beach Escape — Thoughtfully
                            Curated for
                            Relaxation, Comfort, and Unforgettable Moments by the Sea</p>

                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Header Banner -->
    <div
        class="max-w-7xl mx-auto -mt-12 rounded-2xl relative bg-gradient-to-r from-pink-50 to-orange-50 border-b border-gray-200">
        <div class=" px-4 py-5 flex items-center justify-center gap-12">
            <p class="text-gray-700 font-bold">Don't Forget To Book Your Vacation Rentals With Us</p>
            <button
                class="border border-[#004369] hover:bg-orange-600 textColor px-4 py-2 rounded-full text-sm font-medium transition-colors duration-200 flex items-center gap-2">
                View Rentals
                <Icon name="ph:arrow-right" class="text-sm" />
            </button>
        </div>
    </div>

    <!-- Main Content -->
    <div class="max-w-7xl mx-auto px-4 py-8 lg:py-12">
        <div class="grid lg:grid-cols-3 gap-8 lg:gap-12">
            <!-- Contact Form -->
            <div class="col-span-2 bg-gradient-to-br from-[#9ddaec] to-[#abd7e4] rounded-2xl p-6 lg:p-8">
                <h2 class="text-lg lg:text-xl font-bold text-gray-700 text-center mb-8">Contact Us</h2>

                <form class="space-y-6" @submit.prevent="submitForm">
                    <div class="grid md:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-2">First Name *</label>
                            <input v-model="form.firstName" type="text"
                                class="w-full px-4 py-2 bg-white rounded-3xl border border-gray-200 focus:ring-2 focus:ring-[#1B7895] focus:border-transparent outline-none transition-all duration-200"
                                required>
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-2">Last Name *</label>
                            <input v-model="form.lastName" type="text"
                                class="w-full px-4 py-2 bg-white rounded-3xl border border-gray-200 focus:ring-2 focus:ring-[#1B7895] focus:border-transparent outline-none transition-all duration-200"
                                required>
                        </div>
                    </div>

                    <div class="grid md:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-2">Email *</label>
                            <input v-model="form.email" type="email"
                                class="w-full px-4 py-2 bg-white rounded-3xl border border-gray-200 focus:ring-2 focus:ring-[#1B7895] focus:border-transparent outline-none transition-all duration-200"
                                required>
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-2">Phone *</label>
                            <input v-model="form.phone" type="tel"
                                class="w-full px-4 py-2 bg-white rounded-3xl border border-gray-200 focus:ring-2 focus:ring-[#1B7895] focus:border-transparent outline-none transition-all duration-200"
                                required>
                        </div>
                    </div>

                    <div>
                        <label class="block text-sm font-medium text-gray-700 mb-2">Message *</label>
                        <textarea v-model="form.message" rows="6"
                            class="w-full px-4 py-2 bg-white rounded-3xl border border-gray-200 focus:ring-2 focus:ring-[#1B7895] focus:border-transparent outline-none transition-all duration-200 resize-none"
                            required></textarea>
                    </div>

                    <div class="flex items-center gap-2">
                        <input v-model="form.needPetApproval" type="checkbox" id="pet-approval"
                            class="w-4 h-4 textColor bg-gray-100 border-gray-300 rounded focus:ring-[#1B7895]">
                        <label for="pet-approval" class="text-sm text-gray-600">Need Pet Approval?</label>
                    </div>

                    <div class="text-center">
                        <button type="submit"
                            class="bgGradient text-white px-8 py-3 rounded-full font-medium transition-all duration-200 transform hover:scale-105 shadow-lg hover:shadow-xl">
                            Send Message
                        </button>
                    </div>
                </form>
            </div>

            <!-- Contact Information -->
            <div class="space-y-8">
                <div>
                    <h3 class="text-lg lg:text-xl font-bold text-gray-800 mb-6">Special Places of Costa Rica</h3>

                    <div class="space-y-4">
                        <div class="flex items-center gap-3">
                            <div class="w-6 h-6 bg-gray-100 rounded-full flex items-center justify-center">
                                <Icon name="ph:phone" class="text-gray-600 text-lg !size-4" />
                            </div>
                            <span class="text-gray-700 text-sm">(501) 291-5170 (USA #)</span>
                        </div>

                        <div class="flex items-center gap-3">
                            <div class="w-6 h-6 bg-gray-100 rounded-full flex items-center justify-center">
                                <Icon name="ph:phone" class="text-gray-600 text-lg !size-4" />
                            </div>
                            <span class="text-gray-700">+506 2654-4493 (CR #)</span>
                        </div>

                        <div class="flex items-center gap-3">
                            <div class="w-6 h-6 bg-gray-100 rounded-full flex items-center justify-center">
                                <Icon name="ph:envelope" class="text-gray-600 text-lg !size-4" />
                            </div>
                            <span class="text-gray-700">SpecialPlaces@crvr.net</span>
                        </div>

                        <div class="flex items-center gap-3">
                            <div class="w-6 h-6 bg-gray-100 rounded-full flex items-center justify-center">
                                <Icon name="ph:printer" class="text-gray-600 text-lg !size-4" />
                            </div>
                            <span class="text-gray-700">+506 2654-4493</span>
                        </div>

                        <div class="flex items-center gap-3">
                            <div class="w-6 h-6 bg-gray-100 rounded-full flex items-center justify-center">
                                <Icon name="ph:globe" class="text-gray-600 text-lg !size-4" />
                            </div>
                            <span class="text-gray-700">Specialplacesofcostarica</span>
                        </div>
                    </div>
                </div>

                <!-- Social Media Icons -->
                <div class="flex gap-3">
                    <a href="#"
                        class="w-8 h-8 bgGradient  text-white rounded-full flex items-center justify-center transition-colors duration-200">
                        <Icon name="ph:facebook-logo" class="text-lg" />
                    </a>
                    <a href="#"
                        class="w-8 h-8 bgGradient  text-white rounded-full flex items-center justify-center transition-colors duration-200">
                        <Icon name="ph:twitter-logo" class="text-lg" />
                    </a>
                    <a href="#"
                        class="w-8 h-8 bgGradient  text-white rounded-full flex items-center justify-center transition-colors duration-200">
                        <Icon name="ph:linkedin-logo" class="text-lg" />
                    </a>
                    <a href="#"
                        class="w-8 h-8 bgGradient  text-white rounded-full flex items-center justify-center transition-colors duration-200">
                        <Icon name="ph:youtube-logo" class="text-lg" />
                    </a>
                    <a href="#"
                        class="w-8 h-8 bgGradient  text-white rounded-full flex items-center justify-center transition-colors duration-200">
                        <Icon name="ph:share-network" class="text-lg" />
                    </a>
                </div>
            </div>
        </div>
    </div>

    <!-- Help Button -->


    <!-- Scroll to Top Button -->
    <div class="fixed bottom-6 right-12 z-50">
        <button @click="scrollToTop"
            class="bgGradient  text-white w-12 h-12 rounded-full flex items-center justify-center shadow-lg hover:shadow-xl transition-all duration-200 transform hover:scale-110">
            <Icon name="ph:arrow-up" class="text-lg" />
        </button>
    </div>
</template>

<script setup>

// Define page metadata
useHead({
    title: 'Contact Us - Special Places of Costa Rica',
    meta: [
        { name: 'description', content: 'Contact Special Places of Costa Rica for vacation rentals and property management services.' }
    ]
});

// Form data
const form = ref({
    firstName: '',
    lastName: '',
    email: '',
    phone: '',
    message: '',
    needPetApproval: false
});

// Submit form handler
const submitForm = () => {
    // Here you would typically handle the form submission
    // For example, sending the data to your backend API
    console.log('Form submitted:', form.value);

    // You might want to show a success message or redirect
    // For now, we'll just reset the form
    form.value = {
        firstName: '',
        lastName: '',
        email: '',
        phone: '',
        message: '',
        needPetApproval: false
    };

    // Show success message (you could implement a toast notification here)
    alert('Your message has been sent. We will get back to you soon!');
};

// Scroll to top function
const scrollToTop = () => {
    window.scrollTo({
        top: 0,
        behavior: 'smooth'
    });
};
</script>

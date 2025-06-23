<template>
    <div class="container mx-auto bg-white">
        <!-- Navigation Tabs -->
        <nav class="border-b border-gray-200 sticky top-28 bg-white z-30">
            <div class="flex space-x-8 px-6">
                <button v-for="tab in tabs" :key="tab.id"
                    class="py-4 px-2 text-sm font-medium text-gray-700 hover:text-teal-600"
                    :class="{ 'tab-active': activeTab === tab.id }" @click="scrollSmoothToSection(tab.id)">
                    {{ tab.name }}
                </button>
            </div>
        </nav>

        <div class="flex">
            <!-- Main Content -->
            <div class="flex-1 p-6">
                <!-- Description Section -->
                <section id="description" class="mb-12">
                    <h2 class="text-3xl font-bold text-gray-900 mb-6">DESCRIPTION</h2>
                    <div class="text-gray-600 space-y-4">
                        <p>Welcome to Sweet Tea by Kismet Properties of 30A!</p>
                        <p>Experience beachfront bliss at Sweet Tea, a first-floor condo with breathtaking Gulf views.
                            Step directly onto the sugary sand from your private patio and immerse yourself in the
                            emerald waters of 30A. This comfortable one-bedroom unit offers a fully equipped kitchen,
                            spacious living area, and easy access to both the Gulf and Eastern Dune Lake. Enjoy dolphin
                            sightings from your patio and create unforgettable beach memories.</p>

                        <div v-show="showMoreDescription" class="space-y-4">
                            <p>Key Features:</p>
                            <ul class="list-disc list-inside space-y-2 ml-4">
                                <li>Direct beachfront access with private patio</li>
                                <li>One bedroom, one bathroom layout</li>
                                <li>Fully equipped kitchen with modern appliances</li>
                                <li>Spacious living area with Gulf views</li>
                                <li>Close proximity to Eastern Dune Lake</li>
                                <li>Perfect for dolphin watching and sunset viewing</li>
                            </ul>
                        </div>

                        <button @click="showMoreDescription = !showMoreDescription"
                            class="text-teal-600 hover:text-teal-700 font-medium flex items-center">
                            {{ showMoreDescription ? 'READ LESS' : 'READ MORE' }}
                            <Icon
                                :name="showMoreDescription ? 'material-symbols:keyboard-arrow-up' : 'material-symbols:keyboard-arrow-down'"
                                class="ml-1" />
                        </button>
                    </div>
                </section>

                <!-- Amenities Section -->
                <section id="amenities" class="mb-12">
                    <h2 class="text-3xl font-bold text-gray-900 mb-6">AMENITIES</h2>

                    <div class="bg-white border border-gray-200 rounded-lg p-6 mb-6">
                        <h3 class="text-xl font-semibold text-gray-900 mb-4">BATHROOMS</h3>
                        <div class="grid grid-cols-2 gap-4">
                            <div class="flex items-center">
                                <Icon name="material-symbols:star" class="text-teal-600 mr-2" />
                                <span class="text-gray-700">1 Bathroom</span>
                            </div>
                            <div class="flex items-center">
                                <Icon name="material-symbols:star" class="text-teal-600 mr-2" />
                                <span class="text-gray-700">Bathroom 1 - Toilet</span>
                            </div>
                        </div>
                    </div>

                    <div class="bg-white border border-gray-200 rounded-lg p-6">
                        <h3 class="text-xl font-semibold text-gray-900 mb-4">CHECK-IN TYPE</h3>
                        <div class="flex items-center">
                            <Icon name="material-symbols:key" class="text-teal-600 mr-2" />
                            <span class="text-gray-700">Self Check-in</span>
                        </div>
                    </div>
                </section>

                <!-- Availability Section -->
                <section id="availability" class="mb-12">
                    <h2 class="text-3xl font-bold text-gray-900 mb-6">AVAILABILITY</h2>

                    <div class="mb-6">
                        <div class="flex items-center space-x-4 mb-4">
                            <div class="flex items-center">
                                <div class="w-4 h-4 bg-gray-300 rounded mr-2"></div>
                                <span class="text-sm text-gray-600">Past</span>
                            </div>
                            <div class="flex items-center">
                                <div class="w-4 h-4 bg-teal-600 rounded mr-2"></div>
                                <span class="text-sm text-gray-600">Today</span>
                            </div>
                            <div class="flex items-center">
                                <div class="w-4 h-4 bg-gray-600 rounded mr-2"></div>
                                <span class="text-sm text-gray-600">Available</span>
                            </div>
                            <div class="flex items-center">
                                <div class="w-4 h-4 bg-teal-400 rounded mr-2"></div>
                                <span class="text-sm text-gray-600">Booked</span>
                            </div>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                        <!-- June 2025 Calendar -->
                        <div>
                            <div class="flex items-center justify-between mb-4">
                                <button class="p-2 hover:bg-gray-100 rounded" @click="previousMonth">
                                    <Icon name="material-symbols:chevron-left" />
                                </button>
                                <h3 class="text-lg font-semibold">June 2025</h3>
                                <button class="p-2 hover:bg-gray-100 rounded" @click="nextMonth">
                                    <Icon name="material-symbols:chevron-right" />
                                </button>
                            </div>
                            <div class="grid grid-cols-7 gap-1 text-center">
                                <div v-for="day in daysOfWeek" :key="day" previousMonth
                                    class="text-xs font-medium text-gray-500 p-2">
                                    {{ day }}</div>

                                <!-- June dates -->
                                <div v-for="date in juneCalendarDates" :key="date.day"
                                    :class="getCalendarDateClass(date)" class="calendar-date p-3 rounded text-sm">
                                    {{ date.day }}
                                </div>
                            </div>
                        </div>

                        <!-- July 2025 Calendar -->
                        <div>
                            <div class="flex items-center justify-center mb-4">
                                <h3 class="text-lg font-semibold">July 2025</h3>
                            </div>
                            <div class="grid grid-cols-7 gap-1 text-center">
                                <div v-for="day in daysOfWeek" :key="day" class="text-xs font-medium text-gray-500 p-2">
                                    {{ day }}</div>

                                <!-- July dates -->
                                <div v-for="date in julyCalendarDates" :key="date.day"
                                    :class="getCalendarDateClass(date)" class="calendar-date p-3 rounded text-sm">
                                    {{ date.day }}
                                </div>
                            </div>
                        </div>
                    </div>
                </section>

                <!-- Location Section -->
                <section id="location" class="mb-12">
                    <h2 class="text-3xl font-bold text-gray-900 mb-6">LOCATION</h2>
                    <div class="text-gray-600 mb-6">
                        <p>This one bedroom, one bath unit is located directly on the beach with a private walkway and
                            only five steps down to the white sandy beach and emerald waters of the gulf. The ocean is
                            so close you can see the shells washing up on the shore and dolphins jumping in the surf.
                            Leeward II is located off 30A and on Eastern Lake Drive. You have the gulf and the Eastern
                            Dune Lake right outside your door. Our outside deck is spacious and has lots of seating for
                            watching the morning dolphins, reading, or enjoying the sunset.</p>
                    </div>
                    <iframe
                        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d6891.418183215019!2d-86.00546030365994!3d30.273868899235136!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x8893f27adf435501%3A0x58f4f92a2f0bd3a!2sInlet%20Beach%2C%20FL%2032413%2C%20USA!5e0!3m2!1sen!2sin!4v1750258386523!5m2!1sen!2sin"
                        width="820" height="450" style="border:0;" allowfullscreen loading="lazy"
                        referrerpolicy="no-referrer-when-downgrade"></iframe>


                </section>

                <!-- Cancellation Policy Section -->
                <section id="cancellation" class="mb-12">
                    <h2 class="text-3xl font-bold text-gray-900 mb-6">CANCELLATION POLICY</h2>
                    <div class="text-gray-600 space-y-4">
                        <p>One hundred percent (100.00%) of the total booking charges (less $250.00 cancellation fee)
                            will be refunded if the cancellation is made more than 60 days prior to the arrival date of
                            the reservation. Fifty percent (50.00%) of the total booking charges (less $250.00
                            cancellation fee) will be refunded if the cancellation is made more than 30 days prior to
                            the arrival date of the reservation. For cancellations made within 30 days prior to the
                            arrival date, no refund will be issued.</p>

                        <div v-show="showMoreCancellation" class="space-y-4">
                            <p><strong>Additional Terms:</strong></p>
                            <ul class="list-disc list-inside space-y-2 ml-4">
                                <li>All cancellations must be made in writing via email or certified mail</li>
                                <li>Cancellation fees are non-refundable administrative costs</li>
                                <li>Weather-related cancellations follow the same policy unless deemed unsafe by local
                                    authorities</li>
                                <li>Travel insurance is recommended for protection against unforeseen circumstances</li>
                                <li>No-show reservations are treated as same-day cancellations</li>
                            </ul>
                            <p><strong>Modification Policy:</strong></p>
                            <p>Modifications to existing reservations may be subject to rate differences and
                                availability. A $50 modification fee applies to all changes made within 30 days of
                                arrival.</p>
                        </div>

                        <button @click="showMoreCancellation = !showMoreCancellation"
                            class="text-teal-600 hover:text-teal-700 font-medium flex items-center">
                            {{ showMoreCancellation ? 'READ LESS' : 'READ MORE' }}
                            <Icon
                                :name="showMoreCancellation ? 'material-symbols:keyboard-arrow-up' : 'material-symbols:keyboard-arrow-down'"
                                class="ml-1" />
                        </button>
                    </div>
                </section>

                <!-- Reviews Section -->
                <section id="reviews" class="mb-12">
                    <h2 class="text-3xl font-bold text-gray-900 mb-6">REVIEWS</h2>

                    <div class="mb-6">
                        <p class="text-gray-600">Showing {{ reviewRange }} of {{ totalReviews }} reviews</p>
                    </div>

                    <div class="space-y-6">
                        <div v-for="(review, index) in visibleReviews" :key="index"
                            class="review-card bg-white border border-gray-200 rounded-lg p-6">
                            <div class="flex items-center mb-3">
                                <div class="flex text-yellow-400 mr-2">
                                    <Icon v-for="star in 5" :key="star" name="material-symbols:star" />
                                </div>
                                <span class="text-lg font-semibold text-gray-900">{{ review.title }}</span>
                            </div>
                            <p class="text-gray-600 mb-2">By {{ review.author }} – stayed {{ review.date }}</p>
                            <p class="text-gray-700">{{ review.content }}</p>
                        </div>
                    </div>

                    <!-- Pagination -->
                    <div class="flex items-center justify-center space-x-2 mt-8">
                        <button :disabled="currentPage === 1" @click="prevPage"
                            class="px-3 py-2 text-sm font-medium text-gray-500 bg-white border border-gray-300 rounded-md hover:bg-gray-50 disabled:opacity-50 disabled:cursor-not-allowed">
                            <Icon name="material-symbols:chevron-left" class="mr-1" />
                            Previous
                        </button>

                        <template v-for="page in displayedPages" :key="page">
                            <button v-if="page !== '...'" @click="goToPage(page)" :class="[
                                'px-3 py-2 text-sm font-medium rounded-md',
                                currentPage === page
                                    ? 'text-white bg-teal-600 border border-teal-600'
                                    : 'text-gray-700 bg-white border border-gray-300 hover:bg-gray-50'
                            ]">
                                {{ page }}
                            </button>
                            <span v-else class="px-3 py-2 text-sm font-medium text-gray-500">...</span>
                        </template>

                        <button :disabled="currentPage === totalPages" @click="nextPage"
                            class="px-3 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:bg-gray-50 disabled:opacity-50 disabled:cursor-not-allowed">
                            Next
                            <Icon name="material-symbols:chevron-right" class="ml-1" />
                        </button>
                    </div>
                </section>
            </div>

            <!-- Booking Sidebar -->
            <div class="w-96 bg-gray-50 p-6 border-l border-gray-200 sticky top-36 h-screen overflow-y-auto">
                <div class="bg-teal-100 text-teal-800 text-center py-2 px-4 rounded-lg mb-6 font-semibold">
                    BOOK DIRECT & SAVE
                </div>

                <div class="space-y-4 mb-6">
                    <div class="grid grid-cols-2 gap-4">
                        <div>
                            <label class="block text-sm text-gray-600 mb-1">CHECK IN</label>
                            <input type="date" v-model="checkInDate"
                                class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-teal-500"
                                placeholder="Select date">
                        </div>
                        <div>
                            <label class="block text-sm text-gray-600 mb-1">CHECK OUT</label>
                            <input type="date" v-model="checkOutDate"
                                class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-teal-500"
                                placeholder="Select date">
                        </div>
                    </div>

                    <div>
                        <label class="block text-sm text-gray-600 mb-1">GUESTS</label>
                        <div class="relative">
                            <select v-model="guestCount"
                                class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-teal-500 appearance-none">
                                <option v-for="i in 10" :key="i" :value="i">{{ i }} {{ i === 1 ? 'Guest' : 'Guests' }}
                                </option>
                            </select>
                            <div class="absolute inset-y-0 right-0 flex items-center px-2 pointer-events-none">
                                <Icon name="material-symbols:keyboard-arrow-down" />
                            </div>
                        </div>
                    </div>

                    <button
                        class="w-full bg-teal-600 text-white py-3 rounded-md font-medium hover:bg-teal-700 transition">
                        Check Availability
                    </button>

                    <div class="mt-6 border-t border-gray-300 pt-6">
                        <div class="flex justify-between mb-3">
                            <span class="text-gray-600">Rate</span>
                            <span class="font-semibold">$189.00 / night</span>
                        </div>
                        <div class="flex justify-between mb-3">
                            <span class="text-gray-600">Cleaning Fee</span>
                            <span class="font-semibold">$75.00</span>
                        </div>
                        <div class="flex justify-between mb-3">
                            <span class="text-gray-600">Service Fee</span>
                            <span class="font-semibold">$45.00</span>
                        </div>
                        <div class="flex justify-between mb-3">
                            <span class="text-gray-600">Taxes</span>
                            <span class="font-semibold">$29.00</span>
                        </div>
                        <div class="flex justify-between font-bold text-lg border-t border-gray-300 pt-3">
                            <span>Total</span>
                            <span>$339.00</span>
                        </div>
                    </div>
                </div>

                <div class="bg-white border border-gray-200 rounded-lg p-4 mt-6">
                    <h3 class="font-semibold text-gray-900 mb-2">House Rules</h3>
                    <div class="space-y-2 text-sm text-gray-600">
                        <div class="flex items-start">
                            <Icon name="material-symbols:check-circle" class="text-teal-600 mr-2 mt-0.5" />
                            <span>Check-in after 4:00 PM</span>
                        </div>
                        <div class="flex items-start">
                            <Icon name="material-symbols:check-circle" class="text-teal-600 mr-2 mt-0.5" />
                            <span>Checkout before 10:00 AM</span>
                        </div>
                        <div class="flex items-start">
                            <Icon name="material-symbols:check-circle" class="text-teal-600 mr-2 mt-0.5" />
                            <span>2 guests maximum</span>
                        </div>
                        <div class="flex items-start">
                            <Icon name="material-symbols:check-circle" class="text-teal-600 mr-2 mt-0.5" />
                            <span>No pets allowed</span>
                        </div>
                        <div class="flex items-start">
                            <Icon name="material-symbols:check-circle" class="text-teal-600 mr-2 mt-0.5" />
                            <span>No smoking</span>
                        </div>
                    </div>
                </div>

                <div class="mt-6">
                    <div class="flex items-center space-x-2 mb-4">
                        <button class="flex items-center justify-center bg-gray-100 hover:bg-gray-200 p-2 rounded-full">
                            <Icon name="mdi:facebook" class="text-blue-600 text-xl" />
                        </button>
                        <button class="flex items-center justify-center bg-gray-100 hover:bg-gray-200 p-2 rounded-full">
                            <Icon name="mdi:twitter" class="text-blue-400 text-xl" />
                        </button>
                        <button class="flex items-center justify-center bg-gray-100 hover:bg-gray-200 p-2 rounded-full">
                            <Icon name="mdi:pinterest" class="text-red-600 text-xl" />
                        </button>
                        <button class="flex items-center justify-center bg-gray-100 hover:bg-gray-200 p-2 rounded-full">
                            <Icon name="mdi:email" class="text-gray-600 text-xl" />
                        </button>
                    </div>

                    <button class="flex items-center text-teal-600 hover:text-teal-700">
                        <Icon name="material-symbols:flag" class="mr-1" />
                        Report this property
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

interface Tab {
    id: string;
    name: string;
}

interface CalendarDate {
    day: number;
    status: 'past' | 'today' | 'available' | 'booked';
}

interface Review {
    title: string;
    author: string;
    date: string;
    content: string;
    rating: number;
}

const activeTab = ref('description');
const showMoreDescription = ref(false);
const showMoreCancellation = ref(false);
const checkInDate = ref('');
const checkOutDate = ref('');
const guestCount = ref(1);
const currentPage = ref(1);
const itemsPerPage = 3;
const totalReviews = 132;
const totalPages = Math.ceil(totalReviews / itemsPerPage);

const tabs: Tab[] = [
    { id: 'description', name: 'DESCRIPTION' },
    { id: 'amenities', name: 'AMENITIES' },
    { id: 'availability', name: 'AVAILABILITY' },
    { id: 'location', name: 'LOCATION' },
    { id: 'cancellation', name: 'CANCELLATION POLICY' },
    { id: 'reviews', name: 'REVIEWS' },
];

const daysOfWeek = ['SUN', 'MON', 'TUE', 'WED', 'THU', 'FRI', 'SAT'];

const juneCalendarDates: CalendarDate[] = [
    { day: 1, status: 'past' },
    { day: 2, status: 'past' },
    { day: 3, status: 'past' },
    { day: 4, status: 'past' },
    { day: 5, status: 'past' },
    { day: 6, status: 'past' },
    { day: 7, status: 'past' },
    { day: 8, status: 'past' },
    { day: 9, status: 'past' },
    { day: 10, status: 'past' },
    { day: 11, status: 'past' },
    { day: 12, status: 'past' },
    { day: 13, status: 'past' },
    { day: 14, status: 'past' },
    { day: 15, status: 'past' },
    { day: 16, status: 'past' },
    { day: 17, status: 'past' },
    { day: 18, status: 'today' },
    { day: 19, status: 'booked' },
    { day: 20, status: 'booked' },
    { day: 21, status: 'booked' },
    { day: 22, status: 'booked' },
    { day: 23, status: 'booked' },
    { day: 24, status: 'booked' },
    { day: 25, status: 'booked' },
    { day: 26, status: 'booked' },
    { day: 27, status: 'booked' },
    { day: 28, status: 'booked' },
    { day: 29, status: 'booked' },
    { day: 30, status: 'booked' },
];

const julyCalendarDates: CalendarDate[] = [
    { day: 1, status: 'booked' },
    { day: 2, status: 'booked' },
    { day: 3, status: 'booked' },
    { day: 4, status: 'booked' },
    { day: 5, status: 'booked' },
    { day: 6, status: 'booked' },
    { day: 7, status: 'booked' },
    { day: 8, status: 'booked' },
    { day: 9, status: 'booked' },
    { day: 10, status: 'booked' },
    { day: 11, status: 'available' },
    { day: 12, status: 'available' },
    { day: 13, status: 'booked' },
    { day: 14, status: 'booked' },
    { day: 15, status: 'booked' },
    { day: 16, status: 'booked' },
    { day: 17, status: 'booked' },
    { day: 18, status: 'booked' },
    { day: 19, status: 'available' },
    { day: 20, status: 'booked' },
    { day: 21, status: 'booked' },
    { day: 22, status: 'booked' },
    { day: 23, status: 'booked' },
    { day: 24, status: 'booked' },
    { day: 25, status: 'booked' },
    { day: 26, status: 'booked' },
    { day: 27, status: 'booked' },
    { day: 28, status: 'booked' },
    { day: 29, status: 'booked' },
    { day: 30, status: 'booked' },
    { day: 31, status: 'booked' },
];

const allReviews: Review[] = [
    {
        title: 'Wonderful stay',
        author: 'Mel H',
        date: 'Jun 2025',
        content: 'Loved the location.',
        rating: 5
    },
    {
        title: 'Quick getaway',
        author: 'Thurston D',
        date: 'May 2025',
        content: 'Just perfect!',
        rating: 5
    },
    {
        title: 'Great location with clean and comfortable accommodations.',
        author: 'Michael P',
        date: 'Mar 2025',
        content: 'A fun get-away beach experience. We look forward to coming back.',
        rating: 5
    },
    {
        title: 'Perfect beach vacation',
        author: 'Sarah J',
        date: 'Feb 2025',
        content: 'Everything was as described. Beautiful view and easy beach access.',
        rating: 5
    },
    {
        title: 'Relaxing weekend',
        author: 'David L',
        date: 'Jan 2025',
        content: 'Clean, comfortable, and right on the beach. What more could you ask for?',
        rating: 5
    },
    {
        title: 'Amazing property',
        author: 'Jessica R',
        date: 'Dec 2024',
        content: 'We loved our stay! The property was clean and the view was incredible.',
        rating: 5
    },
];

// Computed properties
const visibleReviews = computed(() => {
    const start = (currentPage.value - 1) * itemsPerPage;
    const end = start + itemsPerPage;
    return allReviews.slice(start, end);
});

const reviewRange = computed(() => {
    const start = (currentPage.value - 1) * itemsPerPage + 1;
    const end = Math.min(currentPage.value * itemsPerPage, totalReviews);
    return `${start} - ${end}`;
});

const displayedPages = computed(() => {
    // Always show first page, last page, current page, and pages around current
    if (totalPages <= 7) {
        return Array.from({ length: totalPages }, (_, i) => i + 1);
    }

    const pages = [];
    pages.push(1);

    if (currentPage.value > 3) {
        pages.push('...');
    }

    // Pages around current
    const rangeStart = Math.max(2, currentPage.value - 1);
    const rangeEnd = Math.min(totalPages - 1, currentPage.value + 1);

    for (let i = rangeStart; i <= rangeEnd; i++) {
        pages.push(i);
    }

    if (currentPage.value < totalPages - 2) {
        pages.push('...');
    }

    pages.push(totalPages);

    return pages;
});

// Methods
function getCalendarDateClass(date: CalendarDate) {
    switch (date.status) {
        case 'past':
            return 'bg-gray-300 text-gray-600';
        case 'today':
            return 'bg-teal-600 text-white font-semibold';
        case 'available':
            return 'bg-gray-600 text-white';
        case 'booked':
            return 'bg-teal-400 text-white';
    }
}

function previousMonth() {
    // Logic to navigate to previous month
    // Would need API call in real application
}

function nextMonth() {
    // Logic to navigate to next month
    // Would need API call in real application
}

function prevPage() {
    if (currentPage.value > 1) {
        currentPage.value--;
    }
}

function nextPage() {
    if (currentPage.value < totalPages) {
        currentPage.value++;
    }
}

function goToPage(page: number | string) {
    if (typeof page === 'number') {
        currentPage.value = page;
    }
}

function scrollSmoothToSection(sectionId: string) {
    const section = document.getElementById(sectionId);
    if (section) {
        section.scrollIntoView({ behavior: 'smooth' });
    }
}

</script>

<style scoped>
.tab-active {
    border-bottom: 3px solid #14b8a6;
    color: #14b8a6;
}

.calendar-date {
    transition: all 0.2s ease;
}

.calendar-date:hover {
    transform: scale(1.05);
}

.review-card {
    transition: all 0.3s ease;
}

.review-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
}
</style>
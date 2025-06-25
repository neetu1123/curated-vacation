<template>
    <div class="bg-gray-50 py-8">
        <div class="container mx-auto px-4 sm:px-6 lg:px-8 max-w-6xl">
            <div class="grid  lg:gap-24">
               

                <!-- Right Section - FAQ Accordion -->
                <div class="col-span-">
                    <div class="space-y-3">
                        <div v-for="(faq, index) in faqs" :key="index"
                            class="border border-[#4eade4] bg-sky-100 overflow-hidden text-gray-700">
                            <div class="cursor-pointer px-6 py-5 flex items-center justify-between gap-4"
                                @click="toggleFaq(index)">
                                <div class="flex items-center gap-4">
                                    <div
                                        class=" inline-flex items-center justify-center p-1.5">
                                        <Icon  name="mdi:star-four-points" class="!size-4.5 text-[#4eade4]" />
                                    </div>
                                    {{ faq.question }}
                                </div>
                                <Icon :name="activeFaq === index ? 'lucide:minus' : 'lucide:plus'"
                                    class="size-5 transition-transform" />
                            </div>
                            <div class="overflow-hidden transition-all border-[#4eade4] duration-1000 ease-in-out text-gray-700"
                                :class="{ 'max-h-0 ': activeFaq !== index , 'border-t ': activeFaq === index }"
                                :style="{ maxHeight: activeFaq === index ? `${faqHeights[index]}px` : '0' }">
                                <div class="p-4 sm:py-5 pt-0 ms-4" ref="answerRefs">
                                    <p >
                                        {{ faq.answer }}
                                    </p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted, nextTick } from 'vue';

// State for tracking active FAQ and heights
const activeFaq = ref(null);
const faqHeights = ref([]);
const answerRefs = ref([]);
const faqs = [
    {
        question: "May I check-in early or check-out late?",
        answer: "Early check-in and late check-out are subject to availability. Please contact us in advance to arrange these services. Additional fees may apply for late check-out requests."
    },
    {
        question: "What is your policy on pets?",
        answer: "We welcome well-behaved pets in designated pet-friendly accommodations. A pet fee applies, and advance notice is required. Please review our complete pet policy for specific guidelines and restrictions."
    },
    {
        question: "Do you offer baby equipment?",
        answer: "Yes, we provide various baby equipment including cribs, high chairs, and baby gates upon request. Please let us know your needs when making your reservation to ensure availability."
    },
    {
        question: "Where will I park?",
        answer: "Complimentary parking is available on-site for all guests. Specific parking assignments will be provided upon check-in. Additional parking options are available for guests with multiple vehicles."
    },
    {
        question: "Do you have cooking utensils?",
        answer: "All our accommodations with kitchens come fully equipped with cooking utensils, cookware, dishes, and basic appliances. A complete inventory list is available upon request."
    },
    {
        question: "Do you provide coffee?",
        answer: "Yes, complimentary coffee and tea are provided in all accommodations. Coffee makers and a starter supply of coffee, tea, and filters are included."
    },
    {
        question: "Can we leave our bags in the apartment before check-in?",
        answer: "Luggage storage is available at the front desk for early arrivals. For security reasons, bags cannot be left in apartments before check-in, but our staff will be happy to securely store them for you."
    },
    {
        question: "Do you provide linens/towels?",
        answer: "Yes, all linens and towels are provided including bed sheets, pillowcases, blankets, bath towels, hand towels, and washcloths. Fresh linens are provided for extended stays."
    }
]


// Calculate heights of all answers after mounting
onMounted(async () => {
    await nextTick();

    // Need to wait for refs to be established
    // and content to be rendered
    await nextTick();

    // Initialize array of heights for transitions
    const elements = document.querySelectorAll('.ms-4');
    faqHeights.value = Array.from(elements).map(el => el.scrollHeight);
});

// Toggle FAQ item open/closed
const toggleFaq = (index) => {
    if (activeFaq.value === index) {
        activeFaq.value = null;
    } else {
        activeFaq.value = index;
    }
};
</script>

<style scoped>
.text-primary {
    @apply  underline;
}

.btn {
    @apply inline-flex items-center justify-center;
}

.size-4\.5 {
    width: 1.125rem;
    height: 1.125rem;
}
</style>

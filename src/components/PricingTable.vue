<script setup>
    import { motion } from "motion-v"

    // Data structure for the pricing tiers
    const pricingPlans = [
    {
        id: 1,
        title: 'Early Bird',
        subtitle: 'For The Fast Ones',
        price: '65',
        features: ['Early Entrance', 'Front seat', 'Complementary Drinks', 'Promo Gift'],
        isRecommended: true
    },
    {
        id: 2,
        title: 'Start up',
        subtitle: 'For The Beginners',
        price: '85',
        features: ['Early Entrance', 'Front seat', 'Complementary Drinks', 'Promo Gift'],
        isRecommended: false
    },
    {
        id: 3,
        title: 'Corporate',
        subtitle: 'For The Business',
        price: '95',
        features: ['Early Entrance', 'Front seat', 'Complementary Drinks', 'Promo Gift'],
        isRecommended: false
    }
    ];

    // Entrance Animation for the Header
    const slideUpAnim = {
        initial: { opacity: 0, y: 30 },
        whileInView: { opacity: 1, y: 0, transition: { duration: 0.6, ease: 'easeOut' } }
    };

    // Staggered Entrance Animation for the Pricing Cards
    const cardVariants = {
        initial: { opacity: 0, y: 50 },
        whileInView: (i) => ({
            opacity: 1, 
            y: 0, 
            transition: { 
                type: 'spring', 
                stiffness: 150, 
                damping: 20, 
                delay: i * 0.2 // Stagger effect from left to right
            }
        })
    };
</script>

<template>
    <section class="w-full bg-surface py-24 px-4 sm:px-8 md:px-16 text-[#0f0c29]">
        
        <div class="max-w-[1536px] mx-auto w-full">
        
            <motion.div 
                :initial="slideUpAnim.initial"
                :whileInView="slideUpAnim.whileInView"
                viewport="{ once: true, amount: 0.5 }"
                class="flex flex-col items-center items-start mb-20 text-center text-left"
            >
                <div class="w-10 h-[3px] bg-accent mb-6"></div>
                <h2 class="font-heading font-black text-3xl md:text-4xl lg:text-fluid-h2 uppercase tracking-tight">
                    Pricing Table
                </h2>
            </motion.div>

            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 items-center">
                
                <motion.div 
                    v-for="(plan, index) in pricingPlans" 
                    :key="plan.id"
                    :custom="index"
                    :initial="cardVariants.initial"
                    :whileInView="cardVariants.whileInView"
                    viewport="{ once: true, amount: 0.2 }"
                    class="relative flex flex-col items-center text-center px-6 py-12 sm:p-12 transition-all duration-300 group"
                    :class="[
                        plan.isRecommended 
                        ? 'bg-surface shadow-[0_20px_50px_rgba(0,0,0,0.1)] z-10 lg:scale-105' 
                        : 'bg-muted hover:shadow-lg'
                    ]"
                >
                
                    <div 
                        v-if="plan.isRecommended" 
                        class="absolute top-0 left-0 bg-accent text-surface font-heading text-xs sm:text-sm font-bold tracking-wider uppercase py-2 px-6 shadow-md"
                    >
                        Recommended
                    </div>

                    <h3 class="font-heading font-bold text-2xl mt-4">
                        {{ plan.title }}
                    </h3>
                    <p class="font-general text-sm text-[#0f0c29]/50 mt-2 font-light">
                        {{ plan.subtitle }}
                    </p>

                    <div class="font-heading font-black text-6xl my-8 tracking-tighter">
                        {{ plan.price }}<span class="text-3xl text-[#0f0c29]/40 align-top font-medium ml-1">$</span>
                    </div>

                    <ul class="flex flex-col gap-5 mb-10 font-general text-[#0f0c29]/60 text-sm sm:text-base font-light">
                        <li v-for="(feature, idx) in plan.features" :key="idx">
                            {{ feature }}
                        </li>
                    </ul>

                    <button class="mt-auto bg-accent text-surface px-8 py-3 rounded-full font-heading text-sm font-bold tracking-widest uppercase hover:bg-[#0f0c29] transition-colors duration-300 w-max mx-auto shadow-md cursor-pointer">
                        Purchase
                    </button>
                
                </motion.div>

            </div>
        </div>
    </section>
</template>
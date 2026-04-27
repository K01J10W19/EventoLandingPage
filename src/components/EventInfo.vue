<script setup>
    import { motion } from "motion-v"
    import { Calendar, MapPin, User, Ticket } from 'lucide-vue-next'

    // Data structure for the grid items to keep the template clean
    const eventDetails = [
    { 
        id: 1, 
        icon: Calendar, 
        label: 'Date', 
        value: '12-14 February 2026' 
    },
    { 
        id: 2, 
        icon: MapPin, 
        label: 'Location', 
        value: 'Los Angeles, CA.' 
    },
    { 
        id: 3, 
        icon: User, 
        label: 'Speakers', 
        value: 'Natalie James + guests' 
    },
    { 
        id: 4, 
        icon: Ticket, 
        label: 'Tickets', 
        value: '$65 early bird' 
    }
    ];

    // Spring animation for staggered entry when the user scrolls down
    const cardVariants = {
        initial: { opacity: 0, y: 40 },
        animate: (i) => ({
            opacity: 1, 
            y: 0, 
            transition: { 
            type: 'spring', 
            stiffness: 250, 
            damping: 20, 
            delay: i * 0.15 // Stagger effect based on index
            }
        })
    };
</script>

<template>
    <section class="relative z-20 w-full -mt-16 sm:-mt-24">
        
        <div class="relative w-full bg-surface pt-16 pb-12 px-4 sm:px-8 shadow-xl">
        
            <div class="absolute -top-12 left-1/2 -translate-x-1/2 w-[280px] sm:w-[320px] h-12 z-10">
                <div 
                    class="absolute inset-0 bg-surface rounded-t-2xl shadow-[0_-4px_6px_-1px_rgba(0,0,0,0.05)]" 
                    style="transform: perspective(100px) rotateX(15deg); transform-origin: bottom;"
                ></div>
                
                <div class="relative z-10 flex items-center justify-center gap-8 h-full pb-1"></div>
            </div>

            <div class="max-w-[1280px] mx-auto w-full flex justify-center">
                
                <div class="grid grid-cols-1 md:grid-cols-2 gap-x-12 lg:gap-x-24 gap-y-10 sm:gap-y-12 w-max">
                
                    <motion.div 
                        v-for="(item, index) in eventDetails" 
                        :key="item.id"
                        :custom="index"
                        :initial="cardVariants.initial"
                        :whileInView="cardVariants.animate"
                        viewport="{ once: true, amount: 0.3 }"
                        class="flex items-center gap-4 sm:gap-5 w-[260px] sm:w-[280px]"
                    >
                        <component 
                            :is="item.icon" 
                            class="w-10 h-10 sm:w-12 sm:h-12 text-accent stroke-[1.5] shrink-0" 
                        />
                        
                        <div class="flex flex-col">
                            <h3 class="font-heading font-bold text-base tracking-[0.1em] uppercase text-base">
                                {{ item.label }}
                            </h3>
                            <p class="font-general text-sm sm:text-base text-base/70 mt-1 font-light tracking-wide whitespace-nowrap">
                                {{ item.value }}
                            </p>
                        </div>
                        
                    </motion.div>

                </div>
            </div>

        </div>
    </section>
</template>
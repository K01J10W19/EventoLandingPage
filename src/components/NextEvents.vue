<script setup>
    import { motion } from "motion-v"
    import { Calendar } from 'lucide-vue-next'

    // Data structure for the events list
    const nextEvents = [
        {
            id: 1,
            image: 'https://images.unsplash.com/photo-1516450360452-9312f5e86fc7?q=80&w=300&auto=format&fit=crop',
            day: '14',
            month: 'February',
            title: 'Conference in Amsterdam',
            time: '08 AM - 04 PM',
            speaker: 'Daniel Hill'
        },
        {
            id: 2,
            image: 'https://images.unsplash.com/photo-1516450360452-9312f5e86fc7?q=80&w=300&auto=format&fit=crop',
            day: '18',
            month: 'February',
            title: 'Conference in Amsterdam',
            time: '08 AM - 04 PM',
            speaker: 'Daniel Hill'
        },
        {
            id: 3,
            image: 'https://images.unsplash.com/photo-1516450360452-9312f5e86fc7?q=80&w=300&auto=format&fit=crop',
            day: '22',
            month: 'February',
            title: 'Conference in Amsterdam',
            time: '08 AM - 04 PM',
            speaker: 'Daniel Hill'
        }
    ];

    // Entrance Animation for the entire container
    const containerAnim = {
        initial: { opacity: 0, y: 40 },
        whileInView: { opacity: 1, y: 0, transition: { duration: 0.6, ease: 'easeOut' } }
    };

    // Staggered Entrance Animation for each list item
    const rowVariants = {
        initial: { opacity: 0, x: -20 },
        whileInView: (i) => ({
            opacity: 1, 
            x: 0, 
            transition: { 
                type: 'spring', 
                stiffness: 200, 
                damping: 20, 
                delay: i * 0.15 
            }
        })
    };
</script>

<template>
    <section class="w-full bg-surface py-24 px-4 sm:px-8 md:px-16">
        
        <motion.div 
            :initial="containerAnim.initial"
            :whileInView="containerAnim.whileInView"
            viewport="{ once: true, amount: 0.2 }"
            class="max-w-[1536px] mx-auto flex flex-col shadow-2xl"
        >
        
            <div class="bg-accent text-surface px-6 py-5 sm:px-8 sm:py-6 flex items-center gap-4 rounded-t-sm">
                <Calendar class="w-6 h-6 sm:w-8 sm:h-8 stroke-[1.5]" />
                <h2 class="font-heading font-bold text-lg md:text-xl tracking-wide">
                    Next Events Calendar
                </h2>
            </div>

            <div class="bg-muted flex flex-col rounded-b-sm">
                
                <motion.div 
                    v-for="(event, index) in nextEvents" 
                    :key="event.id"
                    :custom="index"
                    :initial="rowVariants.initial"
                    :whileInView="rowVariants.whileInView"
                    viewport="{ once: true, amount: 0.3 }"
                    class="flex flex-col lg:flex-row items-center justify-between p-6 sm:p-8 border-b border-[#0f0c29]/10 last:border-0 gap-6 lg:gap-8 group transition-colors duration-300 hover:bg-[#0f0c29]/5"
                >
                
                    <img 
                        :src="event.image" 
                        :alt="event.title" 
                        class="w-24 h-24 sm:w-28 sm:h-28 object-cover rounded-md shadow-md shrink-0 transition-transform duration-300 group-hover:scale-105"
                    />

                    <div class="flex flex-col items-center justify-center shrink-0 w-24">
                        <span class="font-heading font-black text-4xl sm:text-5xl text-[#0f0c29] tracking-tighter leading-none">
                            {{ event.day }}
                        </span>
                        <span class="font-general text-xs sm:text-sm text-[#0f0c29]/70 uppercase tracking-widest mt-1">
                            {{ event.month }}
                        </span>
                    </div>

                    <div class="flex flex-col items-center lg:items-center text-center flex-1">
                        <h3 class="font-heading font-bold text-lg sm:text-xl text-[#0f0c29] tracking-wide">
                            {{ event.title }}
                        </h3>
                        <p class="font-heading font-bold text-sm text-accent mt-2">
                            {{ event.time }}
                        </p>
                        <p class="font-general text-xs sm:text-sm text-[#0f0c29]/50 font-light mt-1">
                            Speaker: {{ event.speaker }}
                        </p>
                    </div>

                    <div class="flex flex-col sm:flex-row items-center gap-6 shrink-0 mt-4 lg:mt-0">
                        <button class="bg-accent text-surface px-8 py-3 rounded-full font-heading text-xs font-bold uppercase tracking-widest hover:bg-[#0f0c29] transition-colors duration-300 shadow-md cursor-pointer">
                            Read More
                        </button>
                        <a href="#" class="font-heading text-accent text-xs font-bold uppercase tracking-widest hover:text-[#0f0c29] underline underline-offset-4 transition-colors duration-300">
                            Buy Now
                        </a>
                    </div>

                </motion.div>

            </div>

        </motion.div>
    </section>
</template>
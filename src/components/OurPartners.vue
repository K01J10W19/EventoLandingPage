<script setup>
    import { motion } from "motion-v"
    import { Hexagon, Triangle, Circle, Square, Star, Diamond, Cloud, Cpu } from 'lucide-vue-next'

    // Mock data for partners using Lucide icons as logo placeholders.
    // Added 8 items to demonstrate the horizontal scrolling capability.
    const partners = [
        { id: 1, name: 'Hexa Corp', icon: Hexagon },
        { id: 2, name: 'Tri-State', icon: Triangle },
        { id: 3, name: 'O-Ring Inc', icon: Circle },
        { id: 4, name: 'Block Media', icon: Square },
        { id: 5, name: 'Star Tech', icon: Star },
        { id: 6, name: 'Diamond Edge', icon: Diamond },
        { id: 7, name: 'Cloud Nine', icon: Cloud },
        { id: 8, name: 'Core Systems', icon: Cpu },
    ];

    const slideUpAnim = {
        initial: { opacity: 0, y: 30 },
        whileInView: { opacity: 1, y: 0, transition: { duration: 0.6, ease: 'easeOut' } }
    };

    const logoVariants = {
        initial: { opacity: 0, scale: 0.8 },
        whileInView: (i) => ({
            opacity: 1, 
            scale: 1, 
            transition: { 
            type: 'spring', 
            stiffness: 300, 
            damping: 20, 
            delay: i * 0.05 
            }
        })
    };
</script>

<template>
    <section class="w-full bg-muted py-24 px-4 sm:px-8 md:px-16 text-[#0f0c29]">
        
        <div class="max-w-[1536px] mx-auto w-full">
        
            <motion.div 
                :initial="slideUpAnim.initial"
                :whileInView="slideUpAnim.whileInView"
                viewport="{ once: true, amount: 0.5 }"
                class="flex flex-col items-center sm:items-start mb-16 sm:mb-20 text-center sm:text-left"
            >
                <div class="w-10 h-[3px] bg-accent mb-6"></div>
                <h2 class="font-heading font-black text-3xl md:text-4xl lg:text-fluid-h2 uppercase tracking-tight">
                    Our Partners
                </h2>
            </motion.div>

            <div class="relative w-full">
                <div class="grid grid-flow-col auto-cols-[40%] sm:auto-cols-[28%] lg:auto-cols-[16%] gap-6 sm:gap-10 overflow-x-auto snap-x snap-mandatory no-scrollbar pb-8 pt-4 items-center cursor-grab active:cursor-grabbing">
                
                <motion.div 
                    v-for="(partner, index) in partners" 
                    :key="partner.id"
                    :custom="index"
                    :initial="logoVariants.initial"
                    :whileInView="logoVariants.whileInView"
                    viewport="{ once: true, amount: 0.5 }"
                    class="snap-center flex flex-col justify-center items-center opacity-40 grayscale transition-all duration-300 hover:grayscale-0 hover:opacity-100 hover:text-accent hover:-translate-y-2 group"
                >
                    <component 
                        :is="partner.icon" 
                        class="w-16 h-16 sm:w-20 sm:h-20 stroke-[1.5] transition-transform duration-300" 
                    />
                    
                    <span class="font-heading font-bold text-sm sm:text-base uppercase tracking-widest mt-4 text-center">
                        {{ partner.name }}
                    </span>
                    
                </motion.div>

                </div>
            </div>

        </div>
    </section>
</template>

<style scoped>
    /* Utility to hide the scrollbar while keeping the scroll functionality intact */
    .no-scrollbar::-webkit-scrollbar {
        display: none;
    }
    .no-scrollbar {
        -ms-overflow-style: none;  /* IE and Edge */
        scrollbar-width: none;  /* Firefox */
    }
</style>
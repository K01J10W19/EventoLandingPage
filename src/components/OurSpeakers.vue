<script setup>
    import { motion } from "motion-v"

    // Data structure for 8 Speakers using high-quality Unsplash portraits
    const speakers = [
    { id: 1, name: 'Patricia Stone', title: 'CEO Company', image: 'https://images.unsplash.com/photo-1534528741775-53994a69daeb?q=80&w=800&auto=format&fit=crop' },
    { id: 2, name: 'James Oliver', title: 'CEO Company', image: 'https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?q=80&w=800&auto=format&fit=crop' },
    { id: 3, name: 'Carla Banks', title: 'CEO Company', image: 'https://images.unsplash.com/photo-1544005313-94ddf0286df2?q=80&w=800&auto=format&fit=crop' },
    { id: 4, name: 'William Smith', title: 'CEO Company', image: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?q=80&w=800&auto=format&fit=crop' },
    { id: 5, name: 'Sarah Jenkins', title: 'Creative Director', image: 'https://images.unsplash.com/photo-1524504388940-b1c1722653e1?q=80&w=800&auto=format&fit=crop' },
    { id: 6, name: 'Marcus Chen', title: 'Lead Developer', image: 'https://images.unsplash.com/photo-1519085360753-af0119f7cbe7?q=80&w=800&auto=format&fit=crop' },
    { id: 7, name: 'Elena Rostova', title: 'Marketing Head', image: 'https://images.unsplash.com/photo-1438761681033-6461ffad8d80?q=80&w=800&auto=format&fit=crop' },
    { id: 8, name: 'David Kim', title: 'Product Manager', image: 'https://images.unsplash.com/photo-1500648767791-00dcc994a43e?q=80&w=800&auto=format&fit=crop' }
    ];

    // Entrance Animation for the Header
    const slideUpAnim = {
        initial: { opacity: 0, y: 30 },
        whileInView: { opacity: 1, y: 0, transition: { duration: 0.6, ease: 'easeOut' } }
    };

    // Staggered Entrance Animation for the Grid Items
    const gridItemVariants = {
        initial: { opacity: 0, scale: 0.95 },
        whileInView: (i) => ({
            opacity: 1, 
            scale: 1, 
            transition: { 
            duration: 0.5, 
            ease: 'easeOut',
            delay: i * 0.1 // Fast stagger effect
            }
        })
    };
</script>

<template>
    <section class="w-full bg-surface py-24 px-4 sm:px-8 md:px-16">
        
        <div class="max-w-[1536px] mx-auto w-full">
        
            <motion.div 
                :initial="slideUpAnim.initial"
                :whileInView="slideUpAnim.whileInView"
                viewport="{ once: true, amount: 0.5 }"
                class="flex flex-col mb-12 sm:mb-16"
            >
                <div class="w-10 h-[3px] bg-accent mb-6"></div>
                <h2 class="font-heading font-black text-3xl md:text-4xl lg:text-fluid-h2 uppercase tracking-tight text-base">
                    Our Speakers
                </h2>
            </motion.div>

            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-0 w-full group/grid bg-surface">
                
                <motion.div 
                    v-for="(speaker, index) in speakers" 
                    :key="speaker.id"
                    :custom="index"
                    :initial="gridItemVariants.initial"
                    :whileInView="gridItemVariants.whileInView"
                    viewport="{ once: true, amount: 0.1 }"
                    class="relative aspect-[4/5] sm:aspect-[3/4] lg:aspect-[4/5] overflow-hidden group cursor-pointer transition-all duration-500 hover:z-10 group-hover/grid:brightness-[0.3] hover:!brightness-110"
                >
                    <img 
                        :src="speaker.image" 
                        :alt="speaker.name" 
                        class="w-full h-full object-cover transition-transform duration-700 ease-out group-hover:scale-110"
                    />

                    <div 
                        class="absolute bottom-0 left-0 bg-base px-8 py-5 w-[100%] transform translate-y-4 opacity-0 transition-all duration-300 ease-out group-hover:translate-y-0 group-hover:opacity-100 border-t-[3px] border-accent"
                    >
                        <h3 class="font-heading font-bold text-accent text-lg sm:text-xl tracking-wide mb-1">
                        {{ speaker.name }}
                        </h3>
                        <p class="font-general text-surface/80 text-xs sm:text-sm tracking-widest uppercase">
                        {{ speaker.title }}
                        </p>
                    </div>
                
                </motion.div>

            </div>
        </div>
    </section>
</template>
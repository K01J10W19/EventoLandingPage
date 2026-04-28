<script setup>
    import { motion } from "motion-v"

    // Animations
    const slideUpAnim = {
        initial: { opacity: 0, y: 30 },
        whileInView: { opacity: 1, y: 0, transition: { duration: 0.6, ease: 'easeOut' } }
    };

    const staggerContainer = {
        initial: { opacity: 0 },
        whileInView: { 
            opacity: 1, 
            transition: { staggerChildren: 0.2 } 
        }
    };
</script>

<template>
    <div class="w-full flex flex-col">

        <section class="relative w-full py-24 flex justify-center items-center overflow-hidden px-4 sm:px-8 md:px-16">
        
            <div class="absolute inset-0 z-0">
                <img 
                    src="https://images.unsplash.com/photo-1492684223066-81342ee5ff30?q=80&w=200&auto=format&fit=crop" 
                    alt="Concert Crowd" 
                    class="w-full h-full object-cover object-center"
                />
                <div class="absolute inset-0 bg-base/85 mix-blend-multiply"></div>
            </div>

            <div class="relative z-10 w-full max-w-[1536px] flex flex-col lg:flex-row items-center lg:items-start justify-between lg:gap-16">
                
                <motion.div 
                    :initial="slideUpAnim.initial"
                    :whileInView="slideUpAnim.whileInView"
                    viewport="{ once: true, amount: 0.5 }"
                    class="flex flex-col items-center lg:items-start text-center lg:text-left flex-1"
                >
                    <div class="w-10 h-[3px] bg-accent mb-6"></div>
                    <h2 class="font-heading font-black text-3xl md:text-4xl lg:text-fluid-h2 uppercase tracking-tight text-surface">
                        Get Your Tickets
                    </h2>
                    <p class="font-general text-surface sm:mt-8 sm:mb-8 lg:mt-12 lg:mb-0 leading-relaxed font-light max-w-2xl text-sm lg:text-lg">
                        Lorem ipsum dolor sit amet, consectetur adipiscing elit. In rhoncus massa nec gravida tempus. Integer iaculis in aazzzCurabitur a pulvinar nunc. Maecenas laoreet finibus lectus, at volutpat ligula euismod.
                    </p>
                </motion.div>

                <motion.div 
                initial="{ opacity: 0, scale: 0.9 }"
                whileInView="{ opacity: 1, scale: 1, transition: { type: 'spring', stiffness: 200, delay: 0.2 } }"
                viewport="{ once: true, amount: 0.5 }"
                class="shrink-0 lg:mt-12"
                >
                <button class="bg-accent text-surface px-10 py-4 rounded-full font-heading text-sm font-bold tracking-widest uppercase hover:bg-surface hover:text-accent transition-colors duration-300 shadow-lg cursor-pointer">
                    Buy Now
                </button>
                </motion.div>
                
            </div>
        </section>


        

    </div>
</template>
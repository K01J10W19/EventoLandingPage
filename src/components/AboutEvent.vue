<script setup>
    import { motion } from "motion-v"
    import { Mic, Rocket, Megaphone, Clock } from 'lucide-vue-next'

    // Data structure for the features grid
    const features = [
    { 
        id: 1, 
        icon: Mic, 
        title: '9 Speakers', 
        text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. In rhoncus massa nec graviante.' 
    },
    { 
        id: 2, 
        icon: Rocket, 
        title: '8 Hrs Marathon', 
        text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. In rhoncus massa nec graviante.' 
    },
    { 
        id: 3, 
        icon: Megaphone, 
        title: 'Live Broadcast', 
        text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. In rhoncus massa nec graviante.' 
    },
    { 
        id: 4, 
        icon: Clock, 
        title: 'Early Bird', 
        text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. In rhoncus massa nec graviante.' 
    }
    ];

    // Animation Configurations
    const slideUpAnim = {
        initial: { opacity: 0, y: 30 },
        whileInView: { opacity: 1, y: 0, transition: { duration: 0.6, ease: 'easeOut' } }
    };

    const cardVariants = {
        initial: { opacity: 0, y: 40 },
        whileInView: (i) => ({
            opacity: 1, 
            y: 0, 
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
    <section class="w-full bg-surface py-24 px-4 sm:px-8 md:px-16 text-base">
        <div class="max-w-[1536px] mx-auto w-full">
        
            <motion.div 
                :initial="slideUpAnim.initial"
                :whileInView="slideUpAnim.whileInView"
                viewport="{ once: true, amount: 0.3 }"
                class="flex flex-col mb-12 sm:mb-16"
            >
                <div class="w-10 h-[3px] bg-accent mb-6"></div>
                <h2 class="font-heading font-black text-3xl md:text-4xl lg:text-fluid-h2 uppercase tracking-tight">
                    About The Event
                </h2>
            </motion.div>

            <motion.div 
                :initial="slideUpAnim.initial"
                :whileInView="slideUpAnim.whileInView"
                viewport="{ once: true, amount: 0.3 }"
                class="grid grid-cols-1 md:grid-cols-2 gap-8 md:gap-16 mb-16"
            >
                <p class="font-general text-base/60 leading-relaxed font-light text-sm sm:text-base">
                    Lorem ipsum dolor sit amet, consectetur adipiscing eli. Integer iaculis in 
                    lacus a sollicitudin. Ut hendrerit hendrerit nisl a accumsan. Pellentesque 
                    convallis consectetur tortor id placerat. Curabitur a pulvinar nunc. Maecenas 
                    laoreet finibus lectus, at volutpat ligula euismod.
                </p>
                <p class="font-general text-base/60 leading-relaxed font-light text-sm sm:text-base">
                    In rhoncus massa nec sollicitudin. Ut hendrerit hendrerit nisl a accumsan. 
                    Pellentesque convallis consectetur tortor id placerat. Curabitur a pulvinar 
                    nunc. Maecenas laoreet finibus lectus, at volutpat ligula euismod quis. 
                    Maecenas ornare, ex in malesuada tempus.
                </p>
            </motion.div>

            <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-4 gap-6 sm:gap-8">
                
                <motion.div 
                    v-for="(feature, index) in features" 
                    :key="feature.id"
                    :custom="index"
                    :initial="cardVariants.initial"
                    :whileInView="cardVariants.whileInView"
                    viewport="{ once: true, amount: 0.2 }"
                    class="bg-muted px-6 py-10 sm:p-8 flex flex-col items-start transition-colors duration-300 hover:bg-base hover:text-surface group"
                >
                    <component 
                        :is="feature.icon" 
                        class="w-12 h-12 sm:w-14 sm:h-14 text-accent stroke-[1.5] transition-transform duration-500 group-hover:-translate-y-2" 
                    />
                    
                    <h3 class="font-heading font-bold text-xl lg:text-2xl mt-6 sm:mt-8 tracking-wide transition-colors duration-300">
                        {{ feature.title }}
                    </h3>
                    
                    <p class="font-general text-sm text-current/60 mt-4 leading-relaxed font-light flex-grow transition-colors duration-300">
                        {{ feature.text }}
                    </p>
                    
                    <a 
                        href="#" 
                        class="font-heading font-bold text-sm text-accent mt-6 sm:mt-8 uppercase tracking-wider hover:underline underline-offset-4"
                    >
                        Read More
                    </a>
                
                </motion.div>

            </div>

        </div>
    </section>
</template>
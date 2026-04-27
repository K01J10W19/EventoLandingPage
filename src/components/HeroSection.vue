<script setup>
    import { motion } from "motion-v"

    // 1. Background slow zoom (duration in seconds)
    const bgAnim = {
        initial: { scale: 1.1, opacity: 0 },
        animate: { scale: 1, opacity: 1, transition: { duration: 0.5, ease: 'easeOut' } }
    };

    // 2. Decorative Shapes (Spring pop-in with varying delays in seconds)
    const shapeSpring = { type: 'spring', stiffness: 200, damping: 15 };

    const circleTopAnim = {
        initial: { opacity: 0, scale: 0, x: -50, rotate: -45 },
        animate: { opacity: 0.8, scale: 1, x: 0, rotate: 12, transition: { ...shapeSpring, delay: 0.2 } }
    };
    const circleBottomAnim = {
        initial: { opacity: 0, scale: 0, y: 50 },
        animate: { opacity: 0.8, scale: 1, y: 0, transition: { ...shapeSpring, delay: 0.35 } }
    };
    const circleRightAnim = {
        initial: { opacity: 0, scale: 0, x: 50 },
        animate: { opacity: 0.6, scale: 1, x: 0, transition: { ...shapeSpring, delay: 0.5 } }
    };
    const crossLeftAnim = {
        initial: { opacity: 0, scale: 0, rotate: 0 },
        animate: { opacity: 0.9, scale: 1, rotate: 45, transition: { ...shapeSpring, delay: 0.3 } }
    };
    const crossRightAnim = {
        initial: { opacity: 0, scale: 0, rotate: 0 },
        animate: { opacity: 0.8, scale: 1, rotate: 30, transition: { ...shapeSpring, delay: 0.45 } }
    };
    const crossTopAnim = {
        initial: { opacity: 0, scale: 0, rotate: 0 },
        animate: { opacity: 0.7, scale: 1, rotate: 15, transition: { ...shapeSpring, delay: 0.6 } }
    };

    // 3. Main Content Typography (Staggered sequence)
    const textSpring = { type: 'spring', stiffness: 250, damping: 20 };

    const subtitleAnim = {
        initial: { opacity: 0, y: 30 },
        animate: { opacity: 1, y: 0, transition: { ...textSpring, delay: 0.7 } }
    };
    const titleAnim = {
        initial: { opacity: 0, y: 50, scale: 0.9 },
        animate: { opacity: 1, y: 0, scale: 1, transition: { type: 'spring', stiffness: 300, damping: 18, delay: 0.85 } }
    };
    const dateAnim = {
        initial: { opacity: 0, y: 20 },
        animate: { opacity: 1, y: 0, transition: { ...textSpring, delay: 1.0 } }
    };
    const buttonAnim = {
        initial: { opacity: 0, scale: 0.5, y: 20 },
        animate: { opacity: 1, scale: 1, y: 0, transition: { type: 'spring', stiffness: 400, damping: 15, delay: 1.15 } }
    };
</script>

<template>
    <section class="relative w-full min-h-[80vh] flex flex-col justify-center items-center overflow-hidden px-4 sm:px-8 py-32 xl:py-40">
        
        <div class="absolute inset-0 z-0">
            <motion.img 
                :initial="bgAnim.initial"
                :animate="bgAnim.animate"
                src="https://images.unsplash.com/photo-1514525253161-7a46d19cd819?q=80&w=2000&auto=format&fit=crop" 
                alt="Live Music Stage Background" 
                class="w-full h-full object-cover object-center origin-center"
            />
            <div class="absolute inset-0 bg-base/85 mix-blend-multiply"></div>
            <div class="absolute inset-0 bg-gradient-to-b from-base/50 via-transparent to-base"></div>
        </div>

        <motion.div :initial="circleTopAnim.initial" :animate="circleTopAnim.animate" class="absolute top-[20%] left-[10%] w-8 h-8 sm:w-12 sm:h-12 border-[4px] sm:border-[6px] border-accent rounded-full"></motion.div>
        <motion.div :initial="circleBottomAnim.initial" :animate="circleBottomAnim.animate" class="absolute bottom-[15%] right-[10%] w-6 h-6 sm:w-10 sm:h-10 border-[3px] sm:border-[5px] border-accent rounded-full"></motion.div>
        <motion.div :initial="circleRightAnim.initial" :animate="circleRightAnim.animate" class="absolute top-[10%] right-[20%] w-10 h-10 sm:w-16 sm:h-16 border-[4px] border-[#8b5cf6] rounded-full"></motion.div>
        
        <motion.div :initial="crossLeftAnim.initial" :animate="crossLeftAnim.animate" class="absolute bottom-[25%] left-[15%] text-[#8b5cf6] font-heading text-5xl sm:text-7xl font-bold">+</motion.div>
        <motion.div :initial="crossRightAnim.initial" :animate="crossRightAnim.animate" class="absolute top-[30%] right-[15%] text-accent font-heading text-4xl sm:text-6xl font-bold">+</motion.div>
        <motion.div :initial="crossTopAnim.initial" :animate="crossTopAnim.animate" class="absolute top-[15%] left-[25%] text-[#8b5cf6] font-heading text-3xl sm:text-4xl font-bold">+</motion.div>

        <div class="relative z-10 flex flex-col items-center text-center gap-6 sm:gap-8 max-w-[1024px] mx-auto w-full">
            
            <motion.p 
                :initial="subtitleAnim.initial"
                :animate="subtitleAnim.animate"
                class="font-heading text-fluid-p uppercase tracking-[0.15em] sm:tracking-[0.2em] text-surface drop-shadow-md font-medium"
            >
                Prepare yourself for the
            </motion.p>

            <motion.h1 
                :initial="titleAnim.initial"
                :animate="titleAnim.animate"
                class="font-heading font-black text-fluid-h1 text-accent uppercase leading-none tracking-tight drop-shadow-[0_4px_20px_rgba(249,0,77,0.4)]"
            >
                Conference
            </motion.h1>

            <motion.p 
                :initial="dateAnim.initial"
                :animate="dateAnim.animate"
                class="font-general text-fluid-p text-surface mt-2 sm:mt-4 tracking-wide font-light drop-shadow-md"
            >
                12-14 February 2026 - Los Angeles, CA.
            </motion.p>

            <motion.button 
                :initial="buttonAnim.initial"
                :animate="buttonAnim.animate"
                class="mt-6 sm:mt-8 bg-accent text-surface px-8 sm:px-12 py-4 rounded-full font-heading text-sm sm:text-base font-bold uppercase tracking-wider hover:bg-surface hover:text-accent transition-all duration-300 shadow-[0_0_20px_rgba(249,0,77,0.5)] hover:shadow-[0_0_30px_rgba(255,255,255,0.6)] cursor-pointer"
            >
                Buy Tickets Now
            </motion.button>
        </div>
    </section>
</template>
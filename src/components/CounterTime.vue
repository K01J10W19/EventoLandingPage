<script setup>
    import { ref, onMounted, onUnmounted } from 'vue';
    import { motion } from "motion-v";

    // 1. Target Date Setup (Matches your event schedule)
    const targetDate = new Date('2027-02-12T08:00:00').getTime();

    // Reactive state to hold the formatted time strings
    const timeLeft = ref({
        weeks: '00',
        days: '00',
        hours: '00',
        minutes: '00',
        seconds: '00'
    });

    let timerInterval;

    // 2. Countdown Logic
    const updateCountdown = () => {
        const now = new Date().getTime();
        const distance = targetDate - now;

        // If the countdown is finished, clear interval and keep at 00
        if (distance < 0) {
            clearInterval(timerInterval);
            return;
        }

        // Time calculations
        const w = Math.floor(distance / (1000 * 60 * 60 * 24 * 7));
        const d = Math.floor((distance % (1000 * 60 * 60 * 24 * 7)) / (1000 * 60 * 60 * 24));
        const h = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const m = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
        const s = Math.floor((distance % (1000 * 60)) / 1000);

        // Pad with leading zeros (e.g., '9' becomes '09')
        timeLeft.value = {
            weeks: String(w).padStart(2, '0'),
            days: String(d).padStart(2, '0'),
            hours: String(h).padStart(2, '0'),
            minutes: String(m).padStart(2, '0'),
            seconds: String(s).padStart(2, '0')
        };
    };

    // 3. Lifecycle Hooks
    onMounted(() => {
        updateCountdown(); // Run immediately so there's no 1-second delay
        timerInterval = setInterval(updateCountdown, 1000);
    });

    onUnmounted(() => {
        // Prevent memory leaks when navigating away from this component
        clearInterval(timerInterval);
    });

    // 4. Animations
    const titleAnim = {
        initial: { opacity: 0, y: -20 },
        whileInView: { opacity: 1, y: 0, transition: { type: 'spring', stiffness: 300, damping: 20 } }
    };

    const boxVariants = {
        initial: { opacity: 0, scale: 0.8, y: 30 },
        whileInView: (i) => ({
            opacity: 1, 
            scale: 1, 
            y: 0, 
            transition: { 
                type: 'spring', 
                stiffness: 300, 
                damping: 15, 
                delay: i * 0.1 // Staggered pop-in based on index
            }
        })
    };
</script>

<template>
    <section class="relative w-full py-24 flex flex-col justify-center items-center overflow-hidden">
        
        <div class="absolute inset-0 z-0">
            <img 
                src="https://images.unsplash.com/photo-1492684223066-81342ee5ff30?q=80&w=2000&auto=format&fit=crop" 
                alt="Big Event Background" 
                class="w-full h-full object-cover object-center"
                @error="(e) => e.target.src = 'https://images.unsplash.com/photo-1514525253161-7a46d19cd819?q=80&w=2000&auto=format&fit=crop'"
            />
            <div class="absolute inset-0 bg-base/85 mix-blend-multiply"></div>
        </div>

        <div class="relative z-10 flex flex-col items-center w-full max-w-[1280px] px-4 sm:px-8">
        
        <motion.h2 
            :initial="titleAnim.initial"
            :whileInView="titleAnim.whileInView"
            viewport="{ once: true, amount: 0.5 }"
            class="font-heading font-bold text-2xl sm:text-3xl lg:text-4xl text-surface tracking-wide mb-12 sm:mb-16 text-center drop-shadow-lg"
        >
            Counter until the big event
        </motion.h2>

        <div class="flex flex-wrap justify-center items-center gap-4 sm:gap-6 w-full">
            
            <motion.div 
                v-for="(val, label, index) in timeLeft" 
                :key="label"
                :custom="index"
                :initial="boxVariants.initial"
                :whileInView="boxVariants.whileInView"
                viewport="{ once: true, amount: 0.5 }"
                class="flex flex-col justify-center items-center bg-accent text-surface w-[96px] h-[96px] sm:w-[120px] sm:h-[120px] lg:w-[144px] lg:h-[144px] shadow-[0_10px_30px_rgba(249,0,77,0.3)] transition-transform duration-300 hover:-translate-y-2"
            >
                <span class="font-heading font-bold text-3xl sm:text-5xl lg:text-6xl tracking-tight leading-none">
                    {{ val }}
                </span>
                <span class="font-general text-xs sm:text-sm lg:text-base font-medium mt-2 sm:mt-3 capitalize tracking-wider opacity-90">
                    {{ label }}
                </span>
            </motion.div>

        </div>

        </div>
    </section>
</template>
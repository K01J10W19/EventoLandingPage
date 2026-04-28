<script setup>
    import { Facebook, Twitter, Instagram, Linkedin, Youtube, Heart } from 'lucide-vue-next'

    // Mock images for the Instagram grid
    const instaImages = [
        'https://images.unsplash.com/photo-1514525253161-7a46d19cd819?q=80&w=200&auto=format&fit=crop',
        'https://images.unsplash.com/photo-1514525253161-7a46d19cd819?q=80&w=200&auto=format&fit=crop',
        'https://images.unsplash.com/photo-1492684223066-81342ee5ff30?q=80&w=200&auto=format&fit=crop',
        'https://images.unsplash.com/photo-1516450360452-9312f5e86fc7?q=80&w=200&auto=format&fit=crop',
        'https://images.unsplash.com/photo-1514525253161-7a46d19cd819?q=80&w=200&auto=format&fit=crop',
        'https://images.unsplash.com/photo-1514525253161-7a46d19cd819?q=80&w=200&auto=format&fit=crop',
    ];

    const footerLinks = [
        { name: 'Contact', href: '#' },
        { name: 'News', href: '#' },
        { name: 'Events', href: '#' },
        { name: 'Speakers', href: '#' },
        { name: 'Home', href: '#' }
    ];
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
    <div class="max-w-[1920px] mx-auto w-full flex flex-col">
        
        <footer class="w-full bg-base py-20 px-4 sm:px-8 md:px-16 border-t border-surface/5">
            
            <motion.div 
                :initial="staggerContainer.initial"
                :whileInView="staggerContainer.whileInView"
                viewport="{ once: true, amount: 0.2 }"
                class="w-full max-w-[1536px] mx-auto grid grid-cols-1 lg:grid-cols-3 gap-16 lg:gap-12"
            >
                
                <motion.div :variants="slideUpAnim" class="flex flex-col">
                    <div class="flex items-baseline mb-6">
                        <span class="font-heading text-4xl italic font-bold tracking-tighter text-surface">
                            Evento
                        </span>
                        <span class="w-2.5 h-2.5 bg-accent rounded-full ml-1"></span>
                    </div>
                    
                    <p class="font-general text-surface/50 text-sm leading-relaxed font-light mb-8 pr-4">
                        Lorem ipsum dolor sit amet, consectetur adipiscing elit. In rhoncus massa nec gravida tempus. Integer iaculis in aazzzCurabitur a pulvinar nunc. Maecenas laoreet finibus lectus, at volutpat ligula euismod.
                    </p>
                    
                    <div class="flex items-center gap-3">
                        <a href="#" class="flex justify-center items-center w-10 h-10 rounded-full border border-accent/50 text-accent hover:bg-accent hover:text-surface transition-colors duration-300">
                        <Facebook class="w-4 h-4" fill="currentColor" />
                        </a>
                        <a href="#" class="flex justify-center items-center w-10 h-10 rounded-full border border-accent/50 text-accent hover:bg-accent hover:text-surface transition-colors duration-300">
                        <Twitter class="w-4 h-4" fill="currentColor" />
                        </a>
                        <a href="#" class="flex justify-center items-center w-10 h-10 rounded-full border border-accent/50 text-accent hover:bg-accent hover:text-surface transition-colors duration-300">
                        <Instagram class="w-4 h-4" />
                        </a>
                        <a href="#" class="flex justify-center items-center w-10 h-10 rounded-full border border-accent/50 text-accent hover:bg-accent hover:text-surface transition-colors duration-300">
                        <Linkedin class="w-4 h-4" fill="currentColor" />
                        </a>
                        <a href="#" class="flex justify-center items-center w-10 h-10 rounded-full border border-accent/50 text-accent hover:bg-accent hover:text-surface transition-colors duration-300">
                        <Youtube class="w-4 h-4" />
                        </a>
                    </div>
                </motion.div>

                <motion.div :variants="slideUpAnim" class="flex flex-col">
                    <div class="w-8 h-[2px] bg-accent mb-4"></div>
                    <h3 class="font-heading font-bold text-lg text-surface uppercase tracking-wider mb-6">
                        Instagram
                    </h3>
                    
                    <div class="grid grid-cols-3 gap-2">
                        <a href="#" v-for="(img, idx) in instaImages" :key="idx" class="relative aspect-square overflow-hidden group">
                            <img 
                                :src="img" 
                                alt="Instagram post" 
                                class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
                            />
                            <div class="absolute inset-0 bg-accent/0 group-hover:bg-accent/40 transition-colors duration-300"></div>
                        </a>
                    </div>
                </motion.div>

                <motion.div :variants="slideUpAnim" class="flex flex-col">
                    <div class="w-8 h-[2px] bg-accent mb-4"></div>
                    <h3 class="font-heading font-bold text-lg text-surface uppercase tracking-wider mb-6">
                        Subscribe To Our Newsletter
                    </h3>
                    
                    <form @submit.prevent class="flex flex-col gap-8">
                        <input 
                            type="email" 
                            placeholder="E-mail here" 
                            class="w-full bg-surface/5 border border-transparent focus:border-accent text-surface px-6 py-4 outline-none font-general text-sm font-light placeholder:text-surface/30 transition-colors duration-300 rounded-sm"
                            required
                        />
                        <button 
                            type="submit" 
                            class="w-full bg-accent text-surface px-6 py-4 font-heading text-sm font-bold tracking-widest uppercase hover:bg-surface hover:text-accent transition-colors duration-300 rounded-full shadow-md cursor-pointer"
                        >
                            Subscribe
                        </button>
                    </form>
                </motion.div>

            </motion.div>
        </footer>

        <div class="w-full bg-base py-4 px-4 sm:px-8 md:px-16 border-t border-surface/10">
            <div class="max-w-[1536px] mx-auto w-full flex flex-col lg:flex-row items-center justify-between gap-6">
                
                <div class="font-general text-xs sm:text-sm text-surface/60 font-light flex items-center flex-wrap justify-center lg:justify-start text-center lg:text-left leading-loose">
                    Copyright ©2026 All Rights Reserved | This Template Is Made With 
                    <Heart class="w-4 h-4 mx-1.5 text-surface inline-block shrink-0" /> 
                    By <a href="#" class="text-surface hover:text-accent transition-colors duration-300 ml-1 font-medium">Colorlib</a>
                </div>

                <nav class="flex items-center justify-center flex-wrap gap-4 md:gap-8 lg:gap-4">
                    <a 
                        v-for="link in footerLinks" 
                        :key="link.name"
                        :href="link.href" 
                        class="font-general text-xs sm:text-sm text-surface/60 hover:text-accent transition-colors duration-300 tracking-wider"
                    >
                        {{ link.name }}
                    </a>
                </nav>

            </div>
        </div>

    </div>
</template>

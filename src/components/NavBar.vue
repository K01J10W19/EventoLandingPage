<script setup>
    import { ref, onMounted, onUnmounted } from 'vue';
    import { Search, Menu, X } from 'lucide-vue-next';

    const isMobileMenuOpen = ref(false);
    const isScrolled = ref(false); // New reactive state for scroll detection

    const navLinks = [
        { name: 'Home', href: '#' },
        { name: 'Speakers', href: '#' },
        { name: 'Events', href: '#' },
        { name: 'News', href: '#' },
        { name: 'Contact', href: '#' },
    ];

    const toggleMenu = () => {
        isMobileMenuOpen.value = !isMobileMenuOpen.value;
    };

    // Function to check scroll depth
    const handleScroll = () => {
        // If scrolled past 50 pixels, trigger the active state
        isScrolled.value = window.scrollY > 50;
    };

    // Add and clean up the scroll event listener
    onMounted(() => {
        window.addEventListener('scroll', handleScroll);
        handleScroll(); // Initialize state on load
    });

    onUnmounted(() => {
        window.removeEventListener('scroll', handleScroll);
    });
</script>

<template>
    <header 
        :class="[
            'fixed top-0 left-0 w-full z-50 transition-all duration-300 ease-in-out px-4 sm:px-8 xl:px-16',
            isScrolled 
                ? 'py-4 bg-base/95 backdrop-blur-md shadow-lg border-b border-surface/10' 
                : 'py-6 sm:py-8 bg-transparent border-b border-transparent'
        ]"
    >
        <nav class="max-w-[1536px] mx-auto flex items-center justify-between">
        
            <div class="flex items-baseline relative z-50">
                <a href="#" class="font-heading text-3xl sm:text-4xl italic font-bold tracking-tighter text-surface">
                    Evento
                </a>
                <span class="w-2.5 h-2.5 sm:w-3 sm:h-3 bg-accent rounded-full ml-1"></span>
            </div>

            <ul class="hidden lg:flex items-center gap-8">
                <li v-for="link in navLinks" :key="link.name">
                    <a 
                        :href="link.href" 
                        class="font-general text-surface text-sm font-medium uppercase tracking-[0.1em] hover:text-accent transition-colors duration-300"
                    >
                        {{ link.name }}
                    </a>
                </li>
            </ul>

            <div class="flex items-center gap-4 sm:gap-6 relative z-50">
        
                <button class="text-surface hover:text-accent transition-colors duration-300 group cursor-pointer p-2">
                    <Search class="w-5 h-5 sm:w-6 sm:h-6" />
                </button>

                <button 
                    @click="toggleMenu"
                    class="lg:hidden text-surface hover:text-accent transition-colors duration-300 p-2"
                >
                    <Menu v-if="!isMobileMenuOpen" class="w-6 h-6 sm:w-7 sm:h-7" />
                    <X v-else class="w-6 h-6 sm:w-7 sm:h-7" />
                </button>

            </div>
        </nav>

        <transition
            enter-active-class="transition duration-300 ease-out"
            enter-from-class="transform -translate-y-4 opacity-0"
            enter-to-class="transform translate-y-0 opacity-100"
            leave-active-class="transition duration-200 ease-in"
            leave-from-class="transform translate-y-0 opacity-100"
            leave-to-class="transform -translate-y-4 opacity-0"
        >
            <div 
                v-show="isMobileMenuOpen" 
                class="absolute top-full left-0 w-full bg-base backdrop-blur-md border-t border-surface/10 lg:hidden shadow-xl"
            >
                <ul class="flex flex-col px-6 py-4 gap-4">
                    <li v-for="link in navLinks" :key="link.name">
                        <a 
                            :href="link.href" 
                            class="block w-full text-surface font-general text-base uppercase tracking-wider py-2 hover:text-accent transition-colors duration-300"
                            @click="isMobileMenuOpen = false"
                        >
                            {{ link.name }}
                        </a>
                    </li>
                </ul>
            </div>
        </transition>
    </header>
</template>
<script setup>
  import { motion } from "motion-v"
  import NavBar from './components/NavBar.vue';
  import HeroSection from './components/HeroSection.vue';
  import EventInfo from './components/EventInfo.vue';
  import CounterTime from './components/CounterTime.vue';
  import AboutEvent from './components/AboutEvent.vue';
  import OurSpeakers from './components/OurSpeakers.vue';
  import PricingTable from './components/PricingTable.vue';
  import NextEvents from './components/NextEvents.vue';
  import OurPartners from './components/OurPartners.vue';
  import CallToAction from './components/CallToAction.vue';
  import FooterSection from './components/FooterSection.vue';
</script>

<template>
  <div class="min-h-screen">
    <NavBar />
    
    <main class="max-w-[1920px] mx-auto w-full">
      <HeroSection />
      <EventInfo />
      <CounterTime />
      <AboutEvent />
      <OurSpeakers />
      <PricingTable />
      <NextEvents />
      <OurPartners />
      <!-- <CallToAction />  -->
    </main>

    <!-- <FooterSection /> -->
  </div>
</template>

<script setup>
import Navbar from "@/components/Navbar.vue";
import Hero from "@/components/Hero.vue";
import HomeCards from "@/components/HomeCards.vue";
import JobsListings from "@/components/JobsListings.vue";
</script>

<template>
    <Navbar />
    <Hero />
    <HomeCards />
    <JobsListings :limit="3" :show-btn="true" />
</template>

<style scoped></style>
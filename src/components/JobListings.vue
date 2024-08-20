<script setup>
import { reactive, onMounted } from "vue";
import JobListing from "./JobListing.vue";
import { RouterLink } from "vue-router";
import axios from "axios";
import PulseLoader from "vue-spinner/src/PulseLoader.vue";

const state = reactive({
    jobs: [],
    isLoading: true
});

defineProps({
    limit: Number,
    showBtn: {
        type: Boolean,
        default: false
    }
});

onMounted(async () => {
    try {
        const res = await axios.get(`${import.meta.env.VITE_BASE_URL}/jobs`);
        state.jobs = res.data;
    } catch (error) {
        console.error("Error fetching jobs", error);
    } finally {
        state.isLoading = false;
    }
});
</script>

<template>
    <section class="bg-blue-50 px-4 py-10">
        <div class="container-xl lg:container m-auto">
            <h1 class="text-3xl font-bold text-green-500 mb-6 text-center capitalize">browse jobs</h1>
            <div v-if="state.isLoading"
                 class="text-center text-gray-500 py-6">
                <PulseLoader />
            </div>
            <div v-else
                 class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <JobListing v-for="job in state.jobs.slice(0, limit || state.jobs.length)"
                            :key="job.id"
                            :job="job" />
            </div>
        </div>
    </section>
    <section v-if="showBtn"
             class="m-auto max-w-lg my-10 px-6">
        <RouterLink to="/jobs"
                    class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700">View All Jobs
        </RouterLink>
    </section>
</template>

<style scoped></style>

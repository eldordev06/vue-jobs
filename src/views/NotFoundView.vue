<script setup>
import { RouterLink, useRouter } from "vue-router";

const router = useRouter()
</script>

<template>
    <section class="text-center flex flex-col justify-center items-center h-96">
        <i class="pi pi-exclamation-triangle text-yellow-500 text-7xl mb-5"></i>
        <h1 class="text-6xl font-bold mb-4">404 Not Found</h1>
        <p class="text-xl mb-5">This page does not exist</p>
        <div class="flex gap-5 mt-6">
            <RouterLink to=""
                        @click="$router.back()"
                        class="text-white bg-green-700 hover:bg-green-900 rounded-md px-3 py-2 flex items-center gap-2">
                <i class="pi pi-arrow-circle-left text-xl"></i>
                <span>Go Back</span>
            </RouterLink>
            <RouterLink to="/"
                        class="text-white bg-green-700 hover:bg-green-900 rounded-md px-3 py-2 flex items-center gap-2">
                <i class="pi pi-home text-xl"></i>
                <span>Home Page</span>
            </RouterLink>
        </div>
    </section>
</template>
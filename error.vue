<template>
    <div
        class="h-screen flex flex-col justify-center items-center text-center px-4 text-slate-700"
    >
        <h2 class="text-2xl md:text-3xl font-bold mb-4 ">
            Sorry, this page is not available
        </h2>
        <span class="mb-8">Maybe the page you are looking for has been moved.</span>

        <div
            v-if="isDev && error"
            class="block mb-5 p-6 text-gray-200 border rounded-lg shadow bg-gray-800 border-gray-700 hover:bg-gray-700"
        >
            <h5
                class="mb-2 text-2xl font-bold tracking-tight text-white"
            >
                Error
            </h5>
            <p class="font-normal text-gray-200">
                <strong>{{ error.statusCode }}</strong> - {{ error.message }}
            </p>
            <div v-if="error.stack" class="mt-4" v-html="error.stack" />
        </div>

        <button
            class="bg-blue-500 text-white font-bold py-2 px-4 rounded hover:bg-blue-700 transition duration-150 ease-in-out"
            @click="navigateTo('/')"
        >
            Home
        </button>
    </div>
</template>
<script setup lang="ts">
import type {NuxtError} from '#app'

const isDev = import.meta.env.DEV

defineProps({
    error: Object as () => NuxtError,
})
</script>

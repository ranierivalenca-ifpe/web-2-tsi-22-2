<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/inertia-vue3';

defineProps({
    'categories': []
})

</script>

<template>
    <Head title="Categories" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">Categories</h2>
        </template>

        <h1>Aqui vão as categorias</h1>
        <ul>
            <li v-for="cat of categories" :key="cat" class="border-b-4 shadow-lg bg-yellow-400 p-2 mb-2 rounded border-red-500">
                {{ cat.title }} <a>&times;</a>
            </li>
        </ul>
    </AuthenticatedLayout>
</template>

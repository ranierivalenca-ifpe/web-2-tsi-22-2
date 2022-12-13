<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, useForm } from '@inertiajs/inertia-vue3';

defineProps({
    'categories': []
})

function deleteCategory(id) {
    if (!confirm('are you sure?')) return
    useForm().delete(
        route(
            'categories.destroy', 
            { 'category': id}
        )
    )
}

const form = useForm({
    title: '',
});

function addCategory() {
    form.post(route('categories.store'), {
        onFinish: () => {
            form.title = ''
        }
    })
}

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
                {{ cat.title }} 
                <a class="cursor-pointer font-bold text-red-500" v-on:click="deleteCategory(cat.id)">&times;</a>
            </li>
        </ul>
        <form v-on:submit.prevent="addCategory()">
            <input type="text" placeholder="title" v-model="form.title">
            <button>Add</button>
        </form>
    </AuthenticatedLayout>
</template>

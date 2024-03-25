<template>
    <Head title="Chirps" />

    <AuthenticatedLayout>
        <div class="max-w-2xl mx-auto p-4 sm:p-6 lg:p-8">

            <div class="mt-6 bg-white shadow-sm rounded-lg divide-y">
                <div class="p-6 flex space-x-2">
                    <form @submit.prevent="form.post(route('categories.store'))">
                        <input v-model="form.name" class="mt-4 w-full text-gray-900 border-gray-300 focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50 rounded-md shadow-sm">
                        <InputError :message="form.errors.message" class="mt-2" />
                        <div class="space-x-2">
                            <PrimaryButton class="mt-4">Save</PrimaryButton>
                        </div>
                    </form>

                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>

<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { useForm, Head } from '@inertiajs/vue3';
import PrimaryButton from "@/Components/PrimaryButton.vue";
import InputError from "@/Components/InputError.vue";


const form = useForm({
    name: '',
});

defineProps(['categories']);

</script>


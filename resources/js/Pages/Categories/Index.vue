<template>
    <Head title="Categories" />

    <AuthenticatedLayout>
        <div class="max-w-2xl mx-auto p-4 sm:p-6 lg:p-8">

            <div class="mt-6 bg-white shadow-sm rounded-lg divide-y">
                <div class="p-6 flex-grow space-x-2">
                    <div class="flex-1" v-if="categories" v-for="category in categories">
                        <div class="flex justify-between items-center">
                            <div>
                                <span class="text-gray-800">{{ category.name }}</span>
                                <small class="ml-2 text-sm text-gray-600">{{ category.created_at }}</small>
                            </div>
                            <Dropdown >
                                <template #trigger>
                                    <button>
                                        <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 text-gray-400" viewBox="0 0 20 20" fill="currentColor">
                                            <path d="M6 10a2 2 0 11-4 0 2 2 0 014 0zM12 10a2 2 0 11-4 0 2 2 0 014 0zM16 12a2 2 0 100-4 2 2 0 000 4z" />
                                        </svg>
                                    </button>
                                </template>
                                <template #content>
                                    <button class="block w-full px-4 py-2 text-left text-sm leading-5 text-gray-700 hover:bg-gray-100 focus:bg-gray-100 transition duration-150 ease-in-out" @click="editing = true">
                                        Edit
                                    </button>
                                    <DropdownLink as="button" :href="route('categories.destroy', category.id)" method="delete">
                                        Delete
                                    </DropdownLink>
                                </template>
                            </Dropdown>
                        </div>
                        <p class="mt-4 text-lg text-gray-900">{{ category.name }}</p>
                    </div>
                    <div class="w-10/12" v-else>
                        Categories table is empty!
                    </div>
                </div>

                <div  class="w-2/12">

                    <Link :href="route('categories.create')" class="btn bg-blue-400 px-10 py-2 mt-1">
                        Add
                    </Link>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>

<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { useForm, Head } from '@inertiajs/vue3';
import {onMounted} from "vue";
import Dropdown from "@/Components/Dropdown.vue";
import DropdownLink from "@/Components/DropdownLink.vue";
import { Link } from '@inertiajs/vue3';


const form = useForm({
    name: '',
});

defineProps(['categories']);

</script>


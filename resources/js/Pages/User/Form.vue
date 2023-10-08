<template>
    <div>
        <form @submit.prevent="submit">
            <div class="mb-3">
                <label for="first_name" class="block mb-2 text-md font-medium">Name</label>
                <input type="text" id="first_name" v-model="form.name"
                    :class="{ 'bg-red-50 border border-red-500 text-red-900 placeholder-red-700 text-sm rounded-lg focus:ring-red-500': errors.name }"
                    class="bg-gray-50 border border-gray-300 text-gray-900 text-md rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5">
                <div v-if="errors.name" class="text-red-500 text-sm">{{ errors.name }}</div>
            </div>
            <div class="mb-3">
                <label for="email" class="block mb-2 text-md font-medium">Email</label>
                <input type="text" id="email" v-model="form.email"
                    :class="{ 'bg-red-50 border border-red-500 text-red-900 placeholder-red-700 text-sm rounded-lg focus:ring-red-500': errors.email }"
                    class="bg-gray-50 border border-gray-300 text-gray-900 text-md rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5">
                <div v-if="errors.email" class="text-red-500 text-sm">{{ errors.email }}</div>
            </div>
            <div class="mb-6">
                <label for="password" class="block mb-2 text-md font-medium">Password</label>
                <input type="password" id="password" v-model="form.password"
                    :class="{ 'bg-red-50 border border-red-500 text-red-900 placeholder-red-700 text-sm rounded-lg focus:ring-red-500': errors.password }"
                    class="bg-gray-50 border border-gray-300 text-gray-900 text-md rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5">
                <div v-if="errors.password" class="text-red-500 text-sm">{{ errors.password }}</div>
            </div>
            <button type="submit"
                class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center">Create</button>
        </form>
    </div>
</template>

<script setup>
import { reactive } from 'vue'
import { router } from '@inertiajs/vue3'

defineProps({ errors: Object })

const form = reactive({
    name: null,
    email: null,
    password: null,
})

function submit() {
    router.post('/users', form)
}
</script>

<style lang="scss" scoped></style>

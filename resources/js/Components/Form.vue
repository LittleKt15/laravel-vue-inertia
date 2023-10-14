<template>
    <div class="container max-w-lg mx-auto bg-gray-50 border border-gray-200 rounded-lg p-10 md:mt-24">
        <div class="flex">
            <div class="text-3xl mb-5">{{ user.id === null || user.id === undefined ? 'Create' : 'Edit' }} User Form</div>
            <div>
                <Link href="/users"
                    class="inline-block text-white bg-gray-600 hover:bg-gray-700 focus:ring-4 focus:ring-gray-200 font-medium rounded-lg text-sm px-5 py-2.5 ms-5">
                Back</Link>
            </div>
        </div>

        <form @submit.prevent="submit">
            <div class="mb-3">
                <label for="name" class="block mb-2 text-md font-medium">Name</label>
                <input type="text" id="name" v-model="form.name"
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
            <div class="mb-3">
                <label for="password" class="block mb-2 text-md font-medium">Password</label>
                <input type="password" id="password" v-model="form.password"
                    :class="{ 'bg-red-50 border border-red-500 text-red-900 placeholder-red-700 text-sm rounded-lg focus:ring-red-500': errors.password }"
                    class="bg-gray-50 border border-gray-300 text-gray-900 text-md rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5">
                <div v-if="errors.password" class="text-red-500 text-sm">{{ errors.password }}</div>
            </div>
            <div class="mb-6">
                <label for="confirm_password" class="block mb-2 text-md font-medium">Confirm Password</label>
                <input type="password" id="confirm_password" v-model="form.confirmPassword"
                    :class="{ 'bg-red-50 border border-red-500 text-red-900 placeholder-red-700 text-sm rounded-lg focus:ring-red-500': errors.confirmPassword }"
                    class="bg-gray-50 border border-gray-300 text-gray-900 text-md rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5">
                <div v-if="errors.confirmPassword" class="text-red-500 text-sm">{{ errors.confirmPassword }}</div>
            </div>
            <button type="submit"
                class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center">{{
                    user.id === null || user.id === undefined ? 'Create' : 'Update' }}</button>
        </form>
    </div>
</template>

<script setup>
import { reactive } from 'vue'
import { router, Link } from '@inertiajs/vue3'

const { user, errors } = defineProps({ user: Object, errors: Object })

const form = reactive({
    name: user.name,
    email: user.email,
    password: null,
    confirmPassword: null,
})

function submit() {
    if (user.id === null || user.id === undefined) {
        router.post('/users', form)
    } else {
        router.put(`/users/${user.id}`, form)
    }
}
</script>

<style lang="scss" scoped></style>

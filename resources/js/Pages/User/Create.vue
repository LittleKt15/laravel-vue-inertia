<template>
    <div class="container mx-auto px-5 mt-5">
        <div class="flex">
            <div class="text-3xl mb-5">Create User Form</div>
            <div>
                <Link href="/users"
                    class="inline-block text-white bg-gray-600 hover:bg-gray-700 focus:ring-4 focus:ring-gray-200 font-medium rounded-lg text-sm px-5 py-2.5 ms-5">
                Back</Link>
            </div>
        </div>

        <div class="grid md:grid-cols-3">
            <div>
                <Form :user="user" :errors="errors"></Form>
            </div>
        </div>
    </div>
</template>

<script setup>
import { Link } from '@inertiajs/vue3'
import Form from '../../Components/Form.vue'

defineProps({ user: Object, errors: Object })
</script>

<style lang="scss" scoped></style>

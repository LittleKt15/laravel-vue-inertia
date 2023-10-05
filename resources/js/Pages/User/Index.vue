<template>
    <div class="container mx-auto px-5 mt-5">
        <div class="flex justify-between">
            <div class="text-3xl mb-5">User List</div>
            <div>
                <Link href="/users/create"
                    class="inline-block text-white bg-blue-600 hover:bg-blue-700 focus:ring-4 focus:ring-blue-200 font-medium rounded-lg text-sm px-5 py-2.5 mr-2 mb-2">Create</Link>
            </div>
        </div>

        <div class="relative overflow-x-auto">
            <div v-if="$page.props.add" class="p-4 mb-4 text-sm text-blue-800 rounded-lg bg-blue-50" role="alert">
                <span class="font-medium text-lg">{{ $page.props.add }}</span>
            </div>
            <div v-if="$page.props.del" class="p-4 mb-4 text-sm text-red-800 rounded-lg bg-red-50" role="alert">
                <span class="font-medium text-lg">{{ $page.props.del }}</span>
            </div>
            <table class="w-full text-sm text-left text-gray-500">
                <thead class="text-xs text-gray-700 uppercase bg-gray-300">
                    <tr>
                        <th scope="col" class="px-6 py-3">
                            ID
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Name
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Email
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Date
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Action
                        </th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="user in users" :key="user.id" class="bg-white border-b">
                        <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap">
                            {{ user.id }}
                        </th>
                        <td class="px-6 py-4">
                            {{ user.name }}
                        </td>
                        <td class="px-6 py-4">
                            {{ user.email }}
                        </td>
                        <td class="px-6 py-4">
                            {{ formatDate(user.created_at) }}
                        </td>
                        <td class="px-6 py-4">
                            <Link :href="`/users/${user.id}/edit`"
                                class="text-white bg-green-500 hover:bg-green-600 focus:ring-4 focus:ring-green-200 font-medium rounded-lg text-sm px-5 py-2.5">Edit</Link>
                            <button @click="destroy(user.id)"
                                class="text-white bg-red-500 hover:bg-red-600 focus:ring-4 focus:ring-red-200 font-medium rounded-lg text-sm px-5 py-2.5 ml-1">Delete</button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>

    </div>
</template>

<script>
import { format } from 'date-fns';

export default {
    // props: ['del'],
    methods: {
        destroy(id) {
            this.$inertia.delete(`/users/${id}`);
        },
        formatDate(date) {
            // return format(new Date(date), 'yyyy-MM-dd HH:mm:ss');
            return format(new Date(date), 'yyyy-MM-dd');
        }
    }
}
</script>

<script setup>
import { Link   } from '@inertiajs/vue3'

defineProps({ users: Object })
</script>

<style lang="scss" scoped></style>

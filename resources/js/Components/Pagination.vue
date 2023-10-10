<template>
    <div class="flex sm:justify-end mt-6">
        <nav aria-label="Page navigation example">
            <ul class="inline-flex -space-x-px text-base h-10">
                <li v-for="(link, index) in users.links" :key="index">
                    <Link :href="link.url" v-html="link.label" v-if="link.url"
                        class="flex items-center justify-center px-4 h-10 ml-0 leading-tight text-gray-500 bg-white border border-gray-300 hover:bg-gray-100 hover:text-gray-700">
                    </Link>
                </li>
            </ul>
        </nav>
    </div>
</template>

<script setup>
import { Link } from '@inertiajs/vue3'

defineProps({ users: Object })
</script>

<style lang="scss" scoped></style>

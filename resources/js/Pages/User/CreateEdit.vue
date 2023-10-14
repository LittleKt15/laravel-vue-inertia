<template>
    <Form :user="user" :errors="errors"></Form>
</template>

<script setup>
import Form from '../../Components/Form.vue'

defineProps({ user: Object, errors: Object })
</script>

<style lang="scss" scoped></style>

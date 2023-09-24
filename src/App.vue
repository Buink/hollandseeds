<template>
    <h2>This is test site for prettier auto deploys</h2><div>Categories:</div><p v-if="!categories">No categories</p><ul v-else><li v-for="cat in categories" :key="cat">{{ cat }}</li></ul><button @click="getCategories">Get categories</button>
</template>

<script setup lang="ts">
import { ref } from "vue"

const categories = ref<Array<string> | undefined>(undefined)

const getCategories = async () => {
    const response = await fetch("http://localhost/api/categories")
    categories.value = await response.json()
}
</script>

<style scoped></style>

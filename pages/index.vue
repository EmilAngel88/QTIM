<script setup lang="ts">
import { ref, computed, watch } from 'vue'
import { useRoute, useRouter } from '#imports'
import PostCard from '@/components/PostCard.vue'
import PaginationButton from '@/components/PaginationButton.vue'

interface Post {
    id: string
    title: string
    preview: string
    createdAt: string
    image: string
    description: string
}

const route = useRoute()
const router = useRouter()

const { data: posts, pending, error } = await useFetch<Post[]>(
    'https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts'
)

const perPage = 8

const currentPage = ref(Number(route.query.page) || 1)

const totalPages = computed(() =>
    posts.value ? Math.ceil(posts.value.length / perPage) : 1
)

const paginatedPosts = computed(() => {
    if (!posts.value) return []
    const start = (currentPage.value - 1) * perPage
    return posts.value.slice(start, start + perPage)
})

const goToPage = (n: number) => {
    currentPage.value = n
    router.push({ query: { ...route.query, page: n } })
}

const prevPage = () => {
    if (currentPage.value > 1) {
        goToPage(currentPage.value - 1)
    }
}

const nextPage = () => {
    if (currentPage.value < totalPages.value) {
        goToPage(currentPage.value + 1)
    }
}

watch(
    () => route.query.page,
    (newPage) => {
        currentPage.value = Number(newPage) || 1
    }
)
</script>

<template>
    <main class="container">
        <div v-if="pending">Загрузка...</div>
        <div v-else>
            <h1 class="posts-title">Articles</h1>
            <div class="posts-list">
                <NuxtLink
                    v-for="post in paginatedPosts"
                    :key="post.id"
                    :to="`/posts/${post.id}`"
                    class="post-link"
                >
                    <PostCard :post="post" />
                </NuxtLink>
            </div>

            <div class="pagination">
                <PaginationButton
                    direction="prev"
                    :disabled="currentPage === 1"
                    @click="prevPage"
                />
                <PaginationButton
                    v-for="n in totalPages"
                    :key="n"
                    :page="n"
                    :isActive="n === currentPage"
                    @click="goToPage(n)"
                />
                <PaginationButton
                    direction="next"
                    :disabled="currentPage === totalPages"
                    @click="nextPage"
                />
            </div>
        </div>
    </main>
</template>

<style scoped>
.container {
    max-width: 1220px;
    margin: 0 auto;
    padding: 120px 0 140px;
}

.posts-list {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 24px;
    margin-bottom: 24px;
}

.posts-title {
    font-size: 84px;
    font-weight: 400;
    color: #101010;
    margin-bottom: 60px;
}

.post-link {
    text-decoration: none;
    color: inherit;
}

.pagination {
    display: flex;
    gap: 8px;
}
</style>

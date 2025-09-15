<script setup lang="ts">
import { useRoute } from '#imports'

interface Post {
    id: string
    title: string
    createdAt: string
    image: string
    description: string
}

const route = useRoute()

const { data: post, pending, error } = await useFetch<Post>(
    `https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/${route.params.id}`
)
</script>

<template>
    <main class="container">
        <div v-if="pending">Загрузка...</div>
        <article v-else-if="post" class="post-detail">
            <h1 class="post-title">{{ post.title }}</h1>

            <div class="post-image">
                <img src="https://picsum.photos/1220/700" :alt="post.title" />
            </div>

            <time class="post-date">
                {{ new Date(post.createdAt).toLocaleDateString() }}
            </time>


            <div class="post-description">
                {{ post.description }}
            </div>
        </article>
    </main>
</template>

<style scoped>
.container {
    max-width: 1220px;
    margin: 0 auto;
}

.post-detail {
    display: flex;
    flex-direction: column;
    gap: 16px;
    margin-bottom: 80px;
}

.post-image img {
    width: 100%;
    height: auto;
    object-fit: cover;
}

.post-date {
    font-size: 14px;
    color: #888;
}

.post-title {
    font-size: 84px;
    margin: 0;
    line-height: 1;
    color: #101010;
}

.post-description {
    width: 800px;
    font-size: 18px;
    line-height: 1.6;
    color: #333;
    white-space: pre-line;
}
</style>

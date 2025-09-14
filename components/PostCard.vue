<script setup lang="ts">
interface Post {
    id: string
    createdAt: string
    title: string
    preview: string
    image: string
    description: string
}

defineProps<{
    post: Post
}>()
</script>

<template>
    <article class="post-card">
        <div class="post-image">
            <img src="https://picsum.photos/640/480" :alt="post.title" />
        </div>

        <div>
            <time class="post-date">
                {{ new Date(post.createdAt).toLocaleDateString() }}
            </time>

            <h2 class="post-title">{{ post.title }}</h2>

            <p class="post-preview">
                {{ post.preview }}
            </p>

            <NuxtLink :to="`/posts/${post.id}`" class="post-link">
                Читать дальше →
            </NuxtLink>
        </div>
    </article>
</template>

<style scoped>
.post-card {
    display: flex;
    flex-direction: column;
    overflow: hidden;
    background: #fff;
    transition: box-shadow 0.2s ease-in-out;
    height: 100%;
}

.post-card:hover {
    .post-link {
        visibility: visible;
    }
}

.post-image img {
    width: 100%;
    height: 200px;
    object-fit: cover;
}

.post-date {
    display: block;
    font-size: 14px;
    color: #888;
    margin-bottom: 8px;
}

.post-title {
    font-size: 20px;
    font-weight: 600;
    margin: 0 0 12px;
    line-height: 1.3;
}

.post-preview {
    font-size: 16px;
    color: #444;
    margin-bottom: 16px;
}

.post-link {
    visibility: hidden;
    font-size: 15px;
    font-weight: 500;
    color: #0070f3;
    text-decoration: none;
    transition: color 0.2s ease;
}

.post-link:hover {
    color: #0055aa;
}
</style>

<script setup lang="ts">
import { defineProps, computed } from 'vue'

const props = defineProps<{
    theme?: 'dark' | 'light'
    as?: 'button' | 'link'
    to?: string
    type?: 'button' | 'submit' | 'reset'
    round?: boolean
}>()

const themeClass = computed(() => {
    return props.theme === 'dark' ? 'btn--dark' : 'btn--light'
})

const shapeClass = computed(() => {
    return props.round ? 'btn--round' : 'btn--pill'
})
</script>

<template>
    <component
        :is="as === 'link' ? 'NuxtLink' : 'button'"
        :to="as === 'link' ? to : undefined"
        :type="as === 'button' ? (type || 'button') : undefined"
        class="btn"
        :class="[themeClass, shapeClass]"
    >
        <slot />
    </component>
</template>

<style scoped>
.btn {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    font-weight: 600;
    font-size: 15px;
    text-decoration: none;
    cursor: pointer;
    transition: background-color .12s ease, box-shadow .12s ease, transform .08s ease;
    border: 1px solid transparent;
}

.btn--round {
    width: 44px;
    height: 44px;
    border-radius: 50%;
    padding: 0;
}

.btn--pill {
    padding: 10px 22px;
    border-radius: 9999px;
}

.btn--light {
    background: #ffffff;
    color: #111111;
    border: 1px solid #e9e9e9;
}

.btn--light:hover {
    background: #f5f5f5;
}

.btn--dark {
    background: #111111;
    color: #ffffff;
    border: 1px solid #111111;
}

.btn--dark:hover {
    background: rgba(0,0,0,0.85);
    box-shadow: 0 8px 24px rgba(0,0,0,0.12);
    transform: translateY(-2px);
}
</style>

<script setup lang="ts">
import { defineProps, defineEmits, computed } from 'vue'

const props = defineProps<{
    page?: number
    direction?: 'prev' | 'next'
    isActive?: boolean
}>()

const emit = defineEmits<{
    (e: 'click'): void
}>()

const label = computed(() => {
    if (props.page) return props.page.toString()
    if (props.direction === 'prev') return '←'
    if (props.direction === 'next') return '→'
    return ''
})
</script>

<template>
    <button
        @click="emit('click')"
        class="pagination-btn"
        :class="{ active: props.isActive, direction: props.direction }"
    >
        {{ label }}
    </button>
</template>

<style scoped>
.pagination-btn {
    min-width: 44px;
    height: 44px;
    padding: 0 10px;
    border-radius: 12px;
    background-color: #F3F3F3;
    border: transparent;
    color: #111111;
    font-size: 14px;
    line-height: 1;
    cursor: pointer;
    transition: background-color 0.2s ease, color 0.2s ease, border-color 0.2s ease;
}

.pagination-btn.direction {
    background: #ffffff;
    border: 1px solid #E8E8E8;
}

.pagination-btn:hover {
    background-color: #E8E8E8;
}

.pagination-btn.active {
    background-color: #111111;
    border-color: #111111;
    color: #ffffff;
}

.pagination-btn:disabled {
    opacity: 0.5;
    cursor: not-allowed;
}

</style>

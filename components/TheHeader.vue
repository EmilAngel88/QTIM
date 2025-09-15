<script setup lang="ts">
import { useRoute } from '#imports'
import BritishIcon from "~/components/BritishIcon.vue";

const route = useRoute()

const navItems = [
    { label: 'Works', to: '/' },
    { label: 'About', to: '/' }
]

const isActive = (to: string) => {
    if (to === '/') return route.path === '/'
    return route.path === to || route.path.startsWith(to)
}
</script>

<template>
    <header class="site-header">
        <div class="site-header__inner">
            <NuxtLink
                to="/"
                class="logo"
            >
                QTIM
            </NuxtLink>

            <div class="header-controls">
                <nav class="nav" aria-label="Main navigation">
                    <ul class="nav__list">
                        <li
                            v-for="item in navItems"
                            :key="item.to"
                            class="nav__item"
                        >
                            <NuxtLink
                                :to="item.to"
                                class="nav__link"
                                :class="{ 'nav__link--active': isActive(item.to) }"
                            >
                                {{ item.label }}
                            </NuxtLink>
                        </li>
                    </ul>
                </nav>

                <BaseButton
                    theme="light"
                    round
                >
                    <BritishIcon/>
                </BaseButton>

                <BaseButton
                    theme="dark"
                    as="link"
                    to="/contact"
                >
                    Let's work
                </BaseButton>
            </div>
        </div>
    </header>
</template>

<style scoped>
.site-header {
    /**/
}

.site-header__inner {
    padding: 28px 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.logo {
    font-size: 28px;
    font-weight: 700;
    color: #111111;
    text-decoration: none;
}

.header-controls {
    display: flex;
    align-items: center;
    gap: 18px;
}

.nav__list {
    display: flex;
    gap: 28px;
    margin-right: 90px;
    align-items: center;
}

.nav__item {
    margin-right: 58px;
}

.nav__item:last-child {
    margin-right: 0;
}

.nav__link {
    padding: 6px 0;
    transition: color .15s ease, border-color .15s ease;
}

.nav__link:hover {
    color: #666666;
}

.nav__link--active {
    color: #111111;
}
</style>

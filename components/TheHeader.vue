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
    <header class="site-header" role="banner">
        <div class="site-header__inner">
            <NuxtLink to="/" class="logo">QTIM</NuxtLink>

            <div class="header-controls">
                <nav class="nav" aria-label="Main navigation">
                    <ul class="nav__list">
                        <li v-for="item in navItems" :key="item.to" class="nav__item">
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

                <BaseButton theme="light" round>
                    <BritishIcon/>
                </BaseButton>

                <BaseButton theme="dark" as="link" to="/contact">
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
    margin: 0 90px 0 0;
    padding: 0;
    list-style: none;
    align-items: center;
}

.nav__item {
    margin-right: 58px;
}

.nav__item:last-child {
    margin-right: 0;
}

.nav__link {
    color: #111111;
    text-decoration: none;
    padding: 6px 0;
    transition: color .15s ease, border-color .15s ease;
}

.nav__link:hover {
    color: #666666;
}

.nav__link--active {
    font-weight: 600;
    color: #111111;
}

.lang-btn {
    width: 44px;
    height: 44px;
    padding: 0;
    border-radius: 50%;
    border: 1px solid #e9e9e9;
    background: #ffffff;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: box-shadow .15s ease, transform .08s ease;
}

.lang-btn:hover {
    box-shadow: 0 6px 18px rgba(0,0,0,0.06);
    transform: translateY(-1px);
}

.lang-btn__flag {
    display: block;
    width: 20px;
    height: 14px;
}

.cta {
    display: inline-block;
    padding: 10px 22px;
    border-radius: 9999px;
    background: #111111;
    color: #ffffff;
    text-decoration: none;
    font-weight: 600;
    font-size: 15px;
    transition: background-color .12s ease, box-shadow .12s ease, transform .08s ease;
}

.cta:hover {
    background: rgba(0,0,0,0.85);
    box-shadow: 0 8px 24px rgba(0,0,0,0.12);
    transform: translateY(-2px);
}
</style>

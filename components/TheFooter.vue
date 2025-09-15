<script setup lang="ts">
import TelegramIcon from "~/components/TelegramIcon.vue";
</script>

<template>
    <footer class="footer">
        <div class="container">
            <div class="footer__inner">
                <div class="footer__left">
                    <p class="footer__question">
                        Is there a project?
                    </p>
                    <h2 class="footer__title">
                        <u>Let’s work <br />
                        together</u>
                    </h2>
                </div>

                <div class="footer__right">
                    <div class="footer__contacts">
                        <p>
                            For all questions
                        </p>
                        <a href="tel:+79202780068">
                            +7 (920) 278—00—68
                        </a>
                        <a href="mailto:qtim@agency.com">
                            qtim@agency.com
                        </a>
                    </div>

                    <div class="footer__office">
                        <p>
                            <strong>Office in Russia</strong>
                        </p>
                        <p>
                            139 Ruben Station Lake <br />
                            Drew, NM 52678
                        </p>

                        <BaseButton theme="dark" round>
                            <TelegramIcon />
                        </BaseButton>
                    </div>

                    <div class="footer__office">
                        <p>
                            <strong>Office in Dubai</strong>
                        </p>
                        <p>
                            139 Ruben Station Lake<br />
                            Drew, NM 52678
                        </p>

                        <BaseButton theme="dark" round>
                            <TelegramIcon />
                        </BaseButton>
                    </div>
                </div>
            </div>

            <div class="footer__go">
                <button>
                    <span>Go</span>
                </button>
            </div>

            <div class="footer__bottom">
                <div class="footer__socials">
                    <a href="#">Facebook</a>
                    <a href="#">Instagram</a>
                    <a href="#">Telegram</a>
                </div>
                <div class="footer__socials">
                    <a href="#">Behance</a>
                    <a href="#">LinkedIn</a>
                    <a href="#">Privacy Policy</a>
                </div>
            </div>
        </div>
    </footer>
</template>

<style scoped>
.footer {
    background: #d8b4f8;
    padding: 60px 0 0;
    color: #111;
    display: flex;
    flex-direction: column;
    overflow: hidden;
}

.container {
    max-width: 1220px;
    margin: 0 auto;
    width: 100%;
}

.footer__inner {
    max-width: 1220px;
    margin-right: auto;
    display: flex;
    justify-content: space-between;
    gap: 40px;
}

.footer__left {
    flex: 1;
    margin-right: auto;
}

.footer__question {
    font-size: 16px;
    color: #333;
    margin-bottom: 56px;
}

.footer__title {
    font-size: 112px;
    font-weight: 400;
    line-height: 1;
}

.footer__title u {
    text-decoration-thickness: 2px;
}

.footer__right {
    flex: 0.5;
    display: flex;
    flex-direction: column;
    gap: 24px;
    font-size: 15px;
}

.footer__contacts {
    margin-top: 100px;
}

.footer__contacts a:hover {
    text-decoration: underline;
}

.footer__office p {
    margin-bottom: 4px;
}

.footer__go {
    display: flex;
    justify-content: center;
    margin-top: 60px;
}

.footer__go button {
    width: 358px;
    height: 358px;
    border-radius: 50%;
    border: none;
    background: #101010;
    color: #fff;
    font-size: 20px;
    cursor: pointer;
    transition: background 0.2s;
    transform: translateY(231px);
}

.footer__go button span {
    position: relative;
    top: -25px;
}

.footer__go button:hover {
    background: #333;
}

.footer__bottom {
    padding: 20px 0;
    max-width: 1220px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    font-size: 14px;
}

.footer__socials {
    display: flex;
    gap: 20px;
}

.footer__socials a {
    position: relative;
    color: #111;
}

.footer__socials a:before {
    content: "";
    position: absolute;
    left: 0;
    bottom: -1px;
    width: 100%;
    height: 1px;
    background-color: #111;
}
</style>

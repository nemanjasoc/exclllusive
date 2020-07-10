<template>
    <header>
        <div class="header-container">
           <button class="hamburger hamburger--slider" type="button" 
                @click="isNavOpen()"
                :class="{ 'is-active': toggleClassIsActive }">
                <span class="hamburger-box">
                    <span class="hamburger-inner"></span>
                </span>
            </button>
        </div>
    </header>
</template>

<script>
import { eventBus } from '../../main';

export default {
    data() {
        return {
            toggleClassIsActive: false
        }
    },
    methods: {
        isNavOpen() {
            this.toggleClassIsActive = !this.toggleClassIsActive;
            let isOpen = this.toggleClassIsActive;
            eventBus.$emit('navCheck', isOpen);
        }
    }
}
</script>

<style lang="scss" scoped>
@import 'src/scss/variables';

header {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    z-index: 100;
    padding: 20px 0;
}

.header-container {
    display: flex;
    padding: 0 10px;
}

.hamburger {
    margin-left: auto;
    pointer-events: auto;
    padding: 10px 10px;
    outline: none;
}

.hamburger.is-active .hamburger-inner {
    background-color: $base-color;

    &::before,
    &::after {
        background-color: $base-color;
    }
}

.hamburger-inner {
    background-color: $base-color;
    height: 1px;

    &::before,
    &::after {
        background-color: $base-color;
        height: 1px;
    }
}
</style>

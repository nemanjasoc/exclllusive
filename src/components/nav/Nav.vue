<template>
    <nav class="nav-menu" :class="{ 'is-active': isNavOpen }">
        <div class="menu-container">
            <ul>
                <li></li>
                <li></li>
                <li></li>
            </ul>
        </div>
    </nav>
</template>

<script>
import { eventBus } from '../../main';

export default {
    data() {
        return {
            isNavOpen: false
        }
    },
    created() {
        eventBus.$on('navCheck', (isOpen) => {
            this.isNavOpen = isOpen;
        });
    }
}
</script>

<style lang="scss" scoped>
.nav-menu {
    display: none;
    z-index: 2;

    animation: 0.5s ease 0s normal forwards 1 show;
    -webkit-animation: 0.5s ease 0s normal forwards 1 show;
    opacity: 0;

    @keyframes show {
        from {
            opacity: 0;
            -webkit-transform: scale(1.2);
        }
        to {
            opacity: 1;
            -webkit-transform: scale(1.0);
        }
    }

    @-webkit-keyframes show {
        from {
            opacity: 0;
            -webkit-transform: scale(1.2);
        }
        to {
            opacity: 1;
            -webkit-transform: scale(1.0);
        }
    }
}

.nav-menu.is-active {
    background-image: url("http://exclllusive.concordsoft.com/static/images/menu-bg.jpg");
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background-size: cover;
    background-position: 84% center;
    background-repeat: no-repeat;
    background-color: rgba(0,0,0,0.9);
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    scroll-snap-align: start;
}
</style>

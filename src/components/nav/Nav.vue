<template>
    <nav class="nav-main-menu" :class="{ 'is-active': isNavOpen }">
        <div class="menu-container">
            <div class="menu-products">
                <ul>
                    <li>
                        <button type="button" class="expand-button">Hazelnut</button>
                    </li>
                    <li></li>
                    <li></li>
                </ul>
            </div>
            <div class="menu-company">
                <ul>
                    <li>About Us</li>
                    <li>Contact</li>
                </ul>
                <div class="address">
                    <span>Pure organic doo</span>
                    <span>Boska Vujica 13</span>
                    <span>24000 Subotica</span>
                </div>
                <button type="button" class="contact-button">Constact us</button>
            </div>
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
@import 'src/scss/mixins';

.nav-main-menu {
    display: none;
    z-index: 2;
    @include show-main-nav-animation;
}

.nav-main-menu.is-active {
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
    z-index: 40;
}

.menu-container {
    display: flex;
    flex-direction: column;
    text-align: center;
}

ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
}

li {
    color: #999;
}

.address {
    display: flex;
    color: #fff;
    flex-direction: column;
    padding: 30px 0;

    span {
        padding: 10px 0;
    }
}

@media only screen and (min-width: 768px) {
    .menu-container {
        align-items: center;
        flex-direction: row;
    }
}
</style>

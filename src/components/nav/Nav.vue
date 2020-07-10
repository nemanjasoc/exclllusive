<template>
    <nav class="nav-main-menu" :class="{ 'is-active': isNavOpen }">
        <div class="menu-container">
            <div class="menu-products">
                <button type="button" class="expand-button" @click="productsMenuIsActive = !productsMenuIsActive">Hazelnut</button>
                <div class="hazelnut-menu" :class="{ 'active': productsMenuIsActive }">
                    <ul>
                        <li>
                            <span>Oil</span>
                        </li>
                        <li>
                            <span>Butter</span>
                        </li>
                        <li>
                            <span>Butter with chocolate</span>
                        </li>
                        <li>
                            <span>Flour</span>
                        </li>
                        <li>
                            <span>Gift box small</span>
                        </li>
                        <li>
                            <span>Gift box big</span>
                        </li>
                    </ul>
                </div>
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
                <button type="button" class="contact-button">
                    <span class="contact">Contact us</span>
                </button>
            </div>
        </div>
    </nav>
</template>

<script>
import { eventBus } from '../../main';

export default {
    data() {
        return {
            isNavOpen: false,
            productsMenuIsActive: false
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
@import 'src/scss/variables';

ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
}

.nav-main-menu {
    display: none;
    z-index: 2;
    @include show-main-nav-animation;

    &.is-active {
        background-image: url("http://exclllusive.concordsoft.com/static/images/menu-bg.jpg");
        height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        position: fixed;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        scroll-snap-align: start;
        z-index: 40;
        overflow-y: auto;
    }
}

.menu-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    height: 100vh;
}

.menu-products {
    margin-top: 90px;
    width: 330px;
}

.expand-button {
    border: none;
    outline: none;
    color: $base-color;
    background: transparent;
    cursor: pointer;
    font-size: 52px;
    padding: 0 0 10px 0;
    @include transition(color .2s);

    &:hover {
        color: #fff;
    }
}

.hazelnut-menu {
    height: 0px;

    @include transition(height .2s);

    &.active {
        height: 372px;

        ul {
            text-align: center;

            li {
                padding: 12px 0;
            
                span {
                    position: relative;
                    font-size: 28px;
                    color: #fff;
                    cursor: pointer;
                    padding: 0 5px;

                    &::before,
                    &::after {
                        content: "";
                        position: absolute;
                        top: 15px;
                        width: 0;
                        height: 1px;
                        border-bottom: 1px solid rgba(143,148,0,0.75);
                        @include transition(width .2s);
                    }

                    &::before {
                        right: 100%;
                    }

                    &::after {
                        left: 100%;
                    }

                    &:hover {
                        &::before,
                        &::after {
                            width: 18px;
                        }
                    }
                }
            }
        }
    }
}

.menu-company {
    text-align: center;
    margin-bottom: 100px;

    ul {
        li {
            font-size: 52px;
            padding: 10px 0;
            color: $base-color;
            cursor: pointer;
            @include transition(color .2s);

            &:hover {
                color: #fff;
            }
        }
    }
}

.menu-company {
    .contact-button {
        display: inline-block;
        position: relative;
        border: none;
        color: #fff;
        font-size: 18px;
        cursor: pointer;
        outline: none;
        background:rgba(177, 156, 167, 0.09);
    }

    .contact {
        display: block;
        padding: 15px 40px;
        text-transform: uppercase;
    }

    .contact-button::before, .contact-button::after {
        content:"";
        width: 0;
        height: 2px;
        position: absolute;
        @include transition(all 0.2s linear);
        background: #fff;
        left: 0;
    }

    .contact::before, .contact::after {
        content:"";
        width: 2px;
        height: 0;
        position: absolute;
        @include transition(all 0.2s linear);
        background: #fff;
    }

    .contact::before {
        left: 0;
        top: 1px;
    }

    .contact::after {
        right: 0;
        top: 1px;
    }

    .contact-button:hover::before, .contact-button:hover::after {
        width: 100%;
    }

    .contact-button:hover .contact::before, .contact-button:hover .contact::after {
        height: 100%;
    }

    .constact-button::before {
        left: 50%;
        top: 0;
        transition-duration: 0.4s;
    }
    
    .constact-button::after {
        left: 50%;
        bottom: 0;
        transition-duration: 0.4s;
    }

    .constact-button .contact::before {
        left: 0;
        top: 50%;
        transition-duration: 0.4s;
    }

    .constact-button .contact::after {
        right: 0;
        top: 50%;
        transition-duration: 0.4s;
    }

    .constact-button:hover::before, .constact-button:hover::after {
        left: 0;
    }
    
    .constact-button:hover .contact::before, .constact-button:hover .contact::after {
        top: 0;
    }
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
        justify-content: space-around;
        width: 100%;
    }

    .menu-products {
        text-align: left;
        margin-top: 0;
    }

    .hazelnut-menu {
        &.active {
            ul {
                text-align: left;

                li {
                    position: relative;
                    cursor: pointer;
                    padding: 12px 0;
                    left: 0px;
                    padding-left: 0px;
                    @include transition(all 0.2s ease);

                    span {         
                        font-size: 28px;
                        color: #fff;

                        &::before,
                        &::after {
                            display: none;
                        }
                    }

                    &::before {
                        content: "";
                        position: absolute;
                        top: 26px;
                        right: 100%;
                        width: 0px;
                        height: 1px;
                        border-bottom: 1px solid rgba(143, 148, 0, 0.75);
                        @include transition(width 0.2s ease);
                    }

                    &:hover {
                        left: 25px;
                        padding-left: 5px;

                        &::before {
                            width: 25px;
                        }
                    }
                }
            }
        }
    }

    .menu-company {
        text-align: left;
        margin-bottom: 25px;
    }
}
</style>

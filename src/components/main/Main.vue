<template>
    <main>
        <section class="section-hazelnut-field">
            <div class="hazelnut-field-main-title" :class="{ 'show': showHazelnut }">
                <h1>Hazelnut</h1>
            </div>
        </section>

        <section class="section-hazelnut">
            <button type="button" class="products-button" v-if="!isNavOpen" @click="navProductsIsActive = !navProductsIsActive">
                <span>+</span>
            </button>
            <nav class="nav-products" :class="{ 'show-nav-products': navProductsIsActive }">
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
            </nav>
            <div class="hazelnut-container">
                <div class="vertical-hazelnut-title" :class="{ 'show': !showHazelnut }">
                    <h2>Hazelnut</h2>
                </div>     
                <img class="hazelnut-img" src="../../assets/images/hazelnut.png" :class="{ 'show': !showHazelnut }">
                <div class="text-one" :class="{ 'show': !showHazelnut }">
                    <h3>Hazelnut</h3>
                    <p>The Hazelnut is the nut of the hazel tree which is also called filberts. 
                    Hazelnuts contain the highest level of vitamin E, 
                    which plays an essential role in preserving healthy nails.</p>
                </div>
                <div class="text-two" :class="{ 'show': !showHazelnut }">
                    <h3>Hazelnut</h3>
                    <p>Hazelnuts are full of unsaturated fats, calcium, magnesium, and vitamin B. 
                    Therefore, they support good heart health, may decrease the risk of cancer, 
                    and assist with muscle.</p>
                </div>
            </div>
        </section>
    </main>
</template>

<script>
import { eventBus } from '../../main';

export default {
    data() {
        return {
            isNavOpen: false,
            showHazelnut: true,
            navProductsIsActive: false
        }
    },
    created() {
        window.addEventListener('scroll', () => {
            let h = document.documentElement, 
                b = document.body,
                st = 'scrollTop',
                sh = 'scrollHeight';
            let scrollPercent = (h[st]||b[st]) / ((h[sh]||b[sh]) - h.clientHeight) * 100;

            if (scrollPercent == 0) {
                this.showHazelnut = true;
            }

            if (scrollPercent == 100) {
                this.showHazelnut = false;
            }

        });

        eventBus.$on('navCheck', (isOpen) => {
            this.isNavOpen = isOpen;
        });
    }
}
</script>

<style lang="scss" scoped>
@import 'src/scss/mixins';
@import 'src/scss/variables';

.section-hazelnut-field {
    background-image: url("../../assets/images/3_BG.jpg");
    height: 100vh;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    display: flex;
    align-items: center;
    justify-content: center;
    scroll-snap-align: start;
    overflow: hidden;
}

.hazelnut-field-main-title {
    display: none;
    @include show-hazelnut-animation;

    &.show {
        display: block;
    }

    h1 {
        font-weight: 300;
        font-size: 72px;
        color: white;
    }
}

.section-hazelnut {
    height: 100vh;
    scroll-snap-align: start;
    position: relative;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
}

.products-button {
    position: absolute;
    left: 40px;
    top: 70px;
    width: 65px;
    height: 65px;
    border-radius: 50%;
    background-color: #000;
    color: #fff;
    font-size: 56px;
    font-weight: 300;
    z-index: 40;
    display: flex;
    justify-content: center;
    align-items: center;
    border: none;
    outline: none;
    cursor: pointer;
}

.nav-products {
    opacity: 0;
    height: 100vh;
    width: 100vw;
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    visibility: hidden;
    color: $base-color;
    z-index: 30;

    &.show-nav-products {
        opacity: 0.85;
        visibility: visible;
        background-color: black;

        ul {
            list-style-type: none;
            margin: 0;
            padding: 0;
            text-align: center;
        }

        li {
            padding: 12px 0;
            
            span {
                position: relative;
                text-transform: uppercase;
                font-size: 17px;
                padding: 0 8px;
                color: $base-color;
                cursor: pointer;
                @include transition(letter-spacing .2s);

                &::before,
                &::after {
                    content: "";
                    position: absolute;
                    top: 8px;
                    width: 0;
                    height: 1px;
                    border-bottom: 1px solid $base-color;
                    @include transition(width .2s);
                }

                &::before {
                    right: 100%;
                }

                &::after {
                    left: 100%;
                }

                &:hover {
                    letter-spacing: 4px;

                    &::before,
                    &::after {
                        width: 20px;
                    }
                }
            }
        }
    }
}

.hazelnut-container {
    position: relative;
    max-width: 1140px;
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
}

.vertical-hazelnut-title {
    display: none;
    @include show-hazelnut-animation;

    &.show {
        display: block;
        position: absolute;
        left: -170px;
        max-width: 1140px;
        z-index: -1;
    }

    h2 {
        font-size: 17vh;
        color: #f2f2f2;
        @include transform(-90deg);
    }
}


.hazelnut-img {
    display: none;
    @include show-hazelnut-animation;

    &.show {
        display: block;
        max-width: 60%;
        height: auto;
    }
}

.text-one {
    display: none;
    @include show-text1-animation-small-screen;

    &.show {
        @include texts;
    }
}

.text-two {
    display: none;
    @include show-text2-animation-small-screen;

    &.show {
        @include texts;
    }
}

@media only screen and (min-width: 768px) {
    .text-one {
        display: none;
        @include show-text1-animation;

        &.show {
            display: block;
            position: absolute;
            top: -26%;
            right: 0;
            max-width: 290px;
            text-align: left;

            h3 {
                &::before {
                    content: "";
                    position: absolute;
                    display: block;
                    border: 1px solid rgba(143, 148, 0, 0.4);
                    width: 50px;
                    height: 154px;
                    border-right: none;
                    border-bottom: none;
                    left: -56px;
                    top: 18px;
                }

                &::after {
                    content: "";
                    position: absolute;
                    display: block;
                    border: 1px solid rgba(143,148,0,0.4);
                    border-radius: 50%;
                    width: 57px;
                    height: 57px;
                    left: -85px;
                    top: 142px;
                }
            }
        }

    }

    .text-two {
        display: none;
        @include show-text2-animation;

        &.show {
            display: block;
            position: absolute;
            max-width: 290px;
            left: 0;
            top: 73%;
            text-align: right;

            h3 {
                &::before {
                    content: "";
                    position: absolute;
                    display: block;
                    border: 1px solid rgba(143,148,0,0.4);
                    width: 46px;
                    height: 55px;
                    border-left: none;
                    border-top: none;
                    right: -56px;
                    bottom: 15px;
                }

                &::after {
                    content: "";
                    position: absolute;
                    display: block;
                    border: 1px solid rgba(143,148,0,0.4);
                    right: -85px;
                    bottom: 43px;
                    border-radius: 50%;
                    width: 57px;
                    height: 57px;
                }
            }
        }

    }
}
</style>

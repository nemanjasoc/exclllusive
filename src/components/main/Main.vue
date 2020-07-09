<template>
    <main>
        <section class="section-hazelnut-field">
            <div class="hazelnut-field-main-title" :class="{ 'show-hazelnut': showHazelnut }">
                <h1>Hazelnut</h1>
            </div>
        </section>

        <section class="section-hazelnut">
            <div class="hazelnut-container">
                <div class="vertical-hazelnut-title">
                    <h2>Hazelnut</h2>
                </div>     
                <img class="hazelnut-img" src="src/assets/images/hazelnut.png">
                <div class="text-one">
                    <h3>Hazelnut</h3>
                    <p>The Hazelnut is the nut of the hazel tree which is also called filberts. 
                    Hazelnuts contain the highest level of vitamin E, 
                    which plays an essential role in preserving healthy nails.</p>
                </div>
                <div class="text-two">
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
            showHazelnut: true
        }
    },
    created() {
        var elementsToShow = document.querySelectorAll('.hazelnut-field');

        window.addEventListener('scroll', () => {
            var h = document.documentElement, 
                b = document.body,
                st = 'scrollTop',
                sh = 'scrollHeight';
            var scrollPercent = (h[st]||b[st]) / ((h[sh]||b[sh]) - h.clientHeight) * 100;

            if (scrollPercent == 0) {
                this.showHazelnut = true;
            }

            if (scrollPercent == 100) {
                this.showHazelnut = false;
            }

            console.log(this.showHazelnut);
        });

        eventBus.$on('navCheck', (isOpen) => {
            this.isNavOpen = isOpen;
        });
    }
}
</script>

<style lang="scss" scoped>
.section-hazelnut-field {
    background-image: url("../../assets/images/3_BG.jpg");
    height: 100vh;
    background-size: cover;
    background-position: 84% center;
    background-repeat: no-repeat;
    display: flex;
    align-items: center;
    justify-content: center;
    scroll-snap-align: start;
    overflow: hidden;
}

.hazelnut-field-main-title {
    display: none;
    animation: 1s ease .5s normal forwards 1 showhazelnut;
    -webkit-animation: 1s ease .5s normal forwards 1 showhazelnut;
    opacity: 0;

    @keyframes showhazelnut {
        from {
            opacity: 0;
            -webkit-transform: scale(1.2);
        }
        to {
            opacity: 1;
            -webkit-transform: scale(1.0);
        }
    }

    @-webkit-keyframes showhazelnut {
        from {
            opacity: 0;
            -webkit-transform: scale(1.2);
        }
        to {
            opacity: 1;
            -webkit-transform: scale(1.0);
        }
    }

    &.show-hazelnut {
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

.vertical-hazelnut-title {
    position: absolute;
    left: -330px;
    max-width: 1140px;
    color: #f2f2f2;
    z-index: -1;
    transform: rotate(-90deg);
    -webkit-transform: rotate(-90deg);
    -moz-transform: rotate(-90deg);
    -ms-transform: rotate(-90deg);
    -o-transform: rotate(-90deg);
    filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=3);

    h2 {
        font-size: 17vh;
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

.hazelnut-img {
    max-width: 60%;
    height: auto;
}

.text-one,
.text-two {
    color: #4d4d4d;
    margin: 0 30px;
    text-align: center;

    h3 {
        position: relative;
        position: relative;
        font-weight: 300;
        color: #999;
        font-size: 30px;
        margin-top: 0;
        margin-bottom: 0;
    }
}

p {
    font-weight: 300;
    line-height: 1.5;
    font-size: 15px;
}

@media only screen and (min-width: 768px) {
    .text-one {
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

    .text-two {
        position: absolute;
        max-width: 290px;
        left: 0;
        top: 86%;
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
</style>

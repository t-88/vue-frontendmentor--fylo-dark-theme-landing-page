<template>
    <footer>
        <img :src="logo" alt="logo" class="logo">
        <div class="text">
            <IconText class="location" align_icon="end" :icon="icons.location" text="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua"/>
            <div class="contact">
                <IconText :icon="icons.phone" text="+1-543-123-4567"/>
                <IconText :icon="icons.email" text="example@fylo.com"/>
            </div>

            <div class="urls">
                <div class="urls-1">
                    <p>About Us</p>
                    <p>Jobs</p>
                    <p>Press</p>
                    <p>Blog</p>
                </div>
                <div class="urls-2">
                    <p>Contact Us</p>
                    <p>Terms</p>
                    <p>Privacy</p>
                </div>
            </div>
            <div class="icons">
                <img v-for="img , index in icons_social" :key="index" :src="img" alt="img" class="social-icon">
            </div>
        </div>
    </footer>
</template>

<script>
import IconText from "./IconText"
export default {
    name: "Footer",
    components: {
        IconText,
    },
    data() {
        return {
            logo: require("../assets/logo.svg"),
            icons: {
                location: require("../assets/icon-location.svg"),
                email: require("../assets/icon-email.svg"),
                phone: require("../assets/icon-phone.svg"),
            },
            icons_social: [
                    require("../assets/facebook.png"),
                    require("../assets/twitter.png"),
                    require("../assets/instagram.png")]
        }
    }
}
</script>

<style lang="scss" scoped>
    @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;700&display=swap');
    * { font-family: 'Open Sans', sans-serif; }

    @import "../shared";
    footer {
        background: hsl(216, 53%, 9%);
        display: flex;
        flex-direction: column;
        color: white;
        line-height: 1.5;

        @include media("<=pc",">tablet") {
            padding: applyMath(200,100,$pc,$tablet)
                    applyMath(50,0,$pc,$tablet)
                    applyMath(50,40,$pc,$tablet)
                    applyMath(100,30,$pc,$tablet);
            font-size: applyMath(16,12,$pc,$tablet);
            gap: 45px;
        }
        @include media("<=tablet",">min-width") {
            padding: applyMath(150,115,$tablet,320)
                     applyMath(95,20,$tablet,320)
                     40px
                     applyMath(40,25,$tablet,320);
            font-size: applyMath(16,11,$tablet,320);
            gap: applyMath(40,25,$tablet,320);
        }
        @include media("<=min-width") {
            padding: 115px 20px 40px 25px;
            font-size: 11px;
            gap: 25px;
        }
    }
    .logo {
        width: applyMath(170,150,$pc,$tablet);

    }

    .text {
        display: grid;
        grid-template-columns: 2fr 2fr 2fr 1fr;
        .contact {
            line-height: 2.5;
            div {
                margin-bottom: applyMath(15,9,$tablet,320);
            }
        }
    }
    .urls {
        display: grid;
        grid-template-columns: 1fr 1fr;
        @include media("<=tablet",">min-width") {
            row-gap: applyMath(20,10,$tablet,320);      
        }
        @include media("<=min-width") {
            row-gap: 10px;      
        }
        P {
            line-height: 2.5;
            cursor: pointer;
            &:hover { font-weight: 800; }
        }
    }

    .text , .urls {
        @include media("<=tablet",">min-width") { grid-template-columns: auto; }
        @include media("<=min-width") { grid-template-columns: auto; }
    }
    .icons {
        .social-icon {
            margin-right: 10px;
            cursor: pointer;
            width: applyMath(32,17,$pc,$tablet);
            @include media("<=tablet",">min-width") {
                width: applyMath(40,25,$tablet,320);
                transform: translateX(applyMath(200,95,$tablet,320));
            }
            @include media("<=min-width") {
                width: 25px;
                transform: translateX(95px);
            }
        }
    }

</style>

<style lang="scss">
.location {
    margin: 0 !important;
    img {
        width: 27px;
    }
}
</style>
<template>
    <div class="Nav-Bar">
        <img :src="img_logo" alt="logo" class="logo">
        <div v-if="show_phone_urls" class="phone_options">
            <p v-for="url , index in urls" :key="index" class="phone_url">{{ url }}</p>
       </div>
        <section class="urls">
            <p v-for="url , index in urls" :key="index" class="url">{{ url }}</p>
            
        </section>
    </div>
</template>

<script>
import Logo from "../assets/logo.svg"
export default {
    name: "NavBar",
    components: {
        Logo
    },
    data() {
        return {
            img_logo: require("../assets/logo.svg"),
            urls: ["Features","Team","Sign In"],

            png_options: require("../assets/meat.png"),
            show_phone_urls: false,
        }
    },
    methods: {

    }
}
</script>

<style lang="scss" scoped>
    @import url('https://fonts.googleapis.com/css2?family=Raleway:wght@400;700&display=swap');
    * { font-family: 'Raleway', sans-serif; }

    @import "../shared";

    .Nav-Bar {
        display: flex;
        justify-content: space-between;       

        padding: applyMath(50,30,$pc,$tablet) 
                 applyMath(50,35,$pc,$tablet) 
                 applyMath(100,70,$pc,$tablet)
                 applyMath(50,35,$pc,$tablet);
        
        @include media("<=tablet",">min-width"){
            padding: 30px
                     applyMath(35,20,$tablet,320)
                     70px
                     applyMath(35,10,$tablet,320);
            
        }
        @include media("<=min-width"){
            padding: 30px 20px 70px 10px;
        }
    
    }
    .logo {
        height: max-content;
        width: applyMath(170,130,$pc,$tablet);
        @include media("<=tablet",">min-width"){
            width: applyMath(130,80,$tablet,320);
        }
        @include media("<=min-width"){
            width: 80px;
        }
    }

    .urls {
        display: flex;
        .url {
            color: white;
            opacity: 0.8;
            cursor: pointer;
            align-self: center;
            
            font-size: applyMath(16,12,$pc,$tablet);
            margin-left: applyMath(60,30,$pc,$tablet);
            @include media("<=tablet",">min-width") {
                font-size: applyMath(12,11,$tablet,320);
                margin-left: applyMath(30,15,$tablet,320);
            }
            @include media("<=min-width") {
                margin-left: 15px;
                font-size: 11px
            }
            &:hover {
                opacity: 1;
                text-decoration: underline;
            }
        }
    }
</style>


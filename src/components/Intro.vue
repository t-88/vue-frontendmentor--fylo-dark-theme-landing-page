<template>
    <div id="Intro">
        <img :src="img_intro" alt="img_intro" class="img-intro">
        <section class="text">
            <h1 class="title">All your files in one secure location, accessible anywhere.</h1>
            <p class="description">Fylo stores all your most important files in one secure location. Access them wherever you need, share and collaborate with friends family, and co-workers. </p>
            <Button text="Get Started"/>
        </section>
    </div>
</template>

<script>
import Button from "./Button"
export default {
    name: "Intro",
    components: {
        Button
    },
    data() {
        return {
            img_intro: require("../assets/illustration-intro.png")
        }
    }
}
</script>

<style lang="scss" scoped>
    @import "../shared";

    @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;700&display=swap');

    #Intro {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
        gap: 40px;
    }
    
    .img-intro {
        width: applyMath(720,500,$pc,$tablet);
        @include media("<=tablet",">min-width") {
            width: applyMath(500,240,$tablet,320);
        }
        @include media("<=min-width") {
            width: 240px;
        }
    }

    .text {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        gap: 22px;
        color:white;
        width: 100%;
    
        .title {
            width: applyMath(700,400,$pc,$tablet);
            font-size: applyMath(40,21,$pc,$tablet);

            @include media("<=tablet",">min-width") {
                width: applyMath(400,200,$tablet,$phone);
                font-size: applyMath(21,16,$tablet,320);
            }
            @include media("<=min-width") {
                width: 195px;
                font-size: 16px;
            }
        }    
        .description {
            font-family: 'Open Sans', sans-serif;
            opacity: 0.8;
            letter-spacing: 1px;

            width: applyMath(630,355,$pc,$tablet); 
            font-size: applyMath(18,15,$pc,$tablet);
            @include media("<=tablet",">min-width") {
                width: applyMath(355,245,$tablet,320); 
                font-size: applyMath(15,11,$tablet,320);
            }  
            @include media("<=min-width") {
                width: 245px;
                font-size: 11px;
            }  
        }
        button {
            padding: applyMath(15,10,$pc,320) applyMath(65,25,$pc,320);
            font-size: applyMath(16,11,$pc,320);
        }
    } 
    

</style>


<template>
    <div class="h-img-h-text"> 
        <img :src="img_path" alt="img">
        <div class="text">
            <h1 class="title">{{ title }}</h1>
                <p v-for="p , index in description" :key="index" class="description">{{ p }}</p>

            <div v-if="url" @mouseenter="urlHover" @mouseleave="urlNoHover" class="url-container">
                <p class="url"> 
                    {{ url }} 
                    <img :src="svg_curr_icon" alt="icon" class="icon">
                </p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "HalfImgHalfText",//fuck it someone should make name genrator for this kind of stuff
    props: {
        img_path: String,
        title: String,
        description: String,
        url: { type: String, default: "" },
    },
    data() {
        return {
            svg_icon_hover: require("../assets/icon-arrow-hover.svg"),
            svg_icon_no_hover: require("../assets/icon-arrow-noHover.svg"),
            svg_curr_icon: "",
        }
    },
    created: function(){
        this.urlNoHover()
    },
    methods: {
        urlHover: function(){
            this.svg_curr_icon = this.svg_icon_hover
        },
        urlNoHover: function(){
            this.svg_curr_icon = this.svg_icon_no_hover
        }
    }
}
</script>

<style lang="scss" scoped>
@import "../shared";
    .h-img-h-text {
        color: white;
        display: grid;
        grid-template-columns: 1fr 1fr;

        @include media("<=tablet") {
            grid-template-columns: auto;
            row-gap: 35px;
            padding: 0 applyMath(40,10,$tablet,0);
        }
    }
    img {
        justify-self: center;
        width: applyMath(630,270,$pc,$tablet);
        @include media("<=tablet",">min-width") { 
            width: applyMath(500,280,$tablet,320);
        }
        @include media("<=min-width"){
            width: 270px;
        }
    }
    .text {
        align-self: center;
        row-gap: applyMath(20,10,$pc,$tablet);
        display: grid;
        .title {
            width: applyMath(450,260,$pc,$tablet);
            font-size: applyMath(45,22,$pc,$tablet);

            @include media("<=tablet") {
                font-size: applyMath(24,16,$tablet,320);
                width: 100%;
            }
        }
        .description {
            line-height: 1.5;
            width: applyMath(650,300,$pc,$tablet);
            font-size: applyMath(18,11,$pc,$tablet);
            @include media("<=tablet") {
                width: 100%;
                font-size: applyMath(14,11,$tablet,320);
                letter-spacing: 0.6px;
            }
        }
        .url-container {
            border-bottom: 1px hsl(176, 68%, 64%) solid;
            color: hsl(176, 68%, 64%);
            width: fit-content;
            padding-bottom: 4px;
            cursor: pointer;
            font-size: applyMath(17,11,$pc,$tablet);
            @include media("<=tablet") {
                font-size: applyMath(14,11,$tablet,320);
                letter-spacing: 0.6px;
            }

            &:hover {
                border-bottom: 1px white solid;
                .url {
                    color: white;
                } 
            }
            .url {
                display: inline-block;
                .icon {
                    padding: 0 0 0 5px;
                    transform: translate(0 , 3px);
                    width: inherit;
                }
            }
        }
    }
</style>
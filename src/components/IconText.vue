<template>
    <div class="icon-text">
        <img :style="{'align-self':align_icon}" :src="icon" alt="icon">
        <p class="text">{{ text }}</p>
    </div>    
</template>

<script>
export default {
    name: "IconText",
    props: {
        icon: String,
        text: String,
        align_icon: { type: String, default: "center" },
    }
}
</script>

<style lang="scss" scoped>
    @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;700&display=swap');
    * { font-family: 'Open Sans', sans-serif; }
    @import "../shared";    
    .icon-text {
        color: white;
        display: flex;
        gap: applyMath(30,10,$pc,$tablet);
        @include media("<=tablet",">min-width") {
            gap: applyMath(30,15,$tablet,320);
        }
    }
    img {
        align-self: center;
        height: applyMath(20,15,$pc,$tablet);
        @include media("<=tablet",">min-width") {
            height: applyMath(22,17,$tablet,320);
        }
    }


</style>
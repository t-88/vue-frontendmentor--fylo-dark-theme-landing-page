<template>
    <div class="card">
        <img :src="img_path" alt="" class="icon">
        <h2 class="title">{{ title }}</h2>
        <p class="description">{{ description }}</p>
    </div>    
</template>

<script>
export default {
    name: "Card",
    props: {
        img_path: String,
        title: String,
        description: String,
    }, 
}
</script>

<style lang="scss" scoped>
    @import "../shared";
    .card {
        color:white;
        text-align: center;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 10px;
        width: 20%;
        justify-self: center;
        
        width: applyMath(420,187,$pc,$tablet);

        @include media("<=tablet") { 
            width: 300px;
        }

    }
    .icon {
        margin-bottom: 10px;

        width: applyMath(100,60,$pc,$tablet);
        @include media("<=tablet") { 
            width: 65px;
        }
    }
    .title {
        font-size: applyMath(24,15,$pc,$tablet);
        @include media("<=tablet") { 
            font-size: 18px
        }
    }
    .description {
        opacity: 0.8;
        line-height: 1.5;

        font-size: applyMath(16,10,$pc,$tablet);
        @include media("<=tablet") { 
            font-size: applyMath(16,14,$tablet,320);
        }
    }
</style>
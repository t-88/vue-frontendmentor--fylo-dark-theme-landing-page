<template>
    <div class="comment-card">
        <p class="comment-text">{{ text }}</p>
        <div class="user-info">
            <img :src="user.img" alt="user img" class="user-img">
            <div class="text">
                <p class="user-name">{{ user.name }}</p>
                <p class="user-jop">{{ user.jop }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "CommentCard",
    props: {
        text: String,
        user: {
            type: Object,
            default: { img: "",name: "",jop: "" }
        }
    },
}
</script>

<style lang="scss" scoped>
@import "../shared";
    .comment-card {
        background: hsl(219, 30%, 18%);
        color:white;
        //width: 29%;
        line-height: 1.5;
        border-radius: 5px;
        box-shadow: #50505026 0 0 17px 2px;

        @include media("<=pc",">tablet"){
            padding: applyMath(40,10,$pc,$tablet) 
                 applyMath(20,5,$pc,$tablet)
                 applyMath(30,10,$pc,$tablet)
                 applyMath(30,10,$pc,$tablet);
        }
        @include media("<=tablet",">min-width") {
            padding: applyMath(20,10,$tablet,320)
        }
        @include media("<=min-width") {
            padding: 10px;
        }

    }
    .comment-text {
        width: 100%;
        letter-spacing: 1px;
        
        font-size: applyMath(17,11,$pc,$tablet);
        @include media("<=tablet",">min-width") {
            font-size: applyMath(13,9,$tablet,320);
        }
        @include media("<=min-width") {
            font-size: 9px;
        }
    }
    .user-info {
        display: flex;
        gap: 10px;
        margin-top: applyMath(40,15,$pc,$tablet);
        $size: 0;
        img {
            border-radius: 100%;
            @include media("<=pc",">tablet") {
                width: applyMath(40,30,$pc,$tablet);;
                height: applyMath(40,30,$pc,$tablet);;            }
            @include media("<=tablet",">min-width") {
                width: applyMath(35,25,$tablet,320);
                height: applyMath(35,25,$tablet,320);
            }
            @include media("<=min-width") {              
                width: 25px;
                height: 25px;
            }
        
        }
        .user-name {
            font-weight: 700;
            font-size: applyMath(14,11,$pc,$tablet);
            @include media("<=tablet",">min-width") {
                font-size: applyMath(13,9,$tablet,320);
            }
            @include media("<=min-width") {
                font-size: 9px
            }

        }
        .user-jop {
            font-size: applyMath(11,7,$pc,$tablet);
            @include media("<=tablet",">min-width") {
                font-size: applyMath(10,8,$tablet,320);
            }
            @include media("<=min-width") {
                font-size: 8px      
            }
        }
    }
</style>
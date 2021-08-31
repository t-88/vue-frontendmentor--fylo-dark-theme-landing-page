<template>
    <div class="contact-form">
        <h1 class="title">Get early access today</h1>
        <p class="description">It only takes a minute to sign up and our free starter tier is extremely generous. If you have any questions, our support team would be happy to help you.</p>
        <div class="input-container">
            <input type="email" placeholder="email@example.com">
            <Button text="Get Started Free"/>
        </div>
    </div>
</template>

<script>
import Button from "./Button"
export default {
    name: "ContactFrom",
    components: {
        Button
    },
    data() {

    }
}
</script>

<style lang="scss" scoped>
@import "../shared";
.contact-form {
    background: hsl(217, 28%, 15%);
    color: white;
    text-align: center;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin: auto;
    box-shadow: #0000001f 0 3px 4px 4px;

    gap: applyMath(30,15,$pc,$tablet);
    padding: applyMath(40,20,$pc,$tablet) applyMath(70,20,$pc,$tablet);
    width: applyMath(1000,420,$pc,$tablet);
    transform: translateY(applyMath(150,90,$pc,$tablet));
    
    @include media("<=tablet",">min-width") {
        width: applyMath(500,290,$tablet,320);
        transform: translateY(applyMath(155,120,$tablet,320));

    }
    @include media("<=min-width") {
        width: 290px;
        transform: translateY(120px);
    }

}
.title {
    font-size: applyMath(35,20,$pc,$tablet);
}
.description {
    width: 70%;
    line-height: 1.5;
    letter-spacing: 1px;

    font-size: applyMath(16,10,$pc,$tablet);
    width: applyMath(732,345,$pc,$tablet);
    @include media("<=min-width") {
        font-size:10px;
        width: 250px;
    }
}
.input-container {
    display: flex;
    gap: 30px;
    width: 100%;
    justify-content: center;

    height: applyMath(50,20,$pc,$tablet);
    @include media("<=tablet",">min-width") {
        flex-direction: column;
        gap: applyMath(15,10,$tablet,320);
        height: auto;
    }
    @include media("<=min-width") {
        flex-direction: column;
        gap: 10px;
        height: auto;
    }

    input {
        width: 60%;
        padding: 0px 20px;
        border-radius: 20px;
        border: transparent;
        outline: transparent;
        color: black;
        
        font-size: applyMath(16,10,$pc,$tablet);
        @include media("<=tablet",">min-width"){ padding: 0 applyMath(20,10,$tablet,320); }
        @include media("<=min-width") { padding: 0 10px; }
    }
    ::placeholder { letter-spacing: 1px; }
    button {
        width: 25%;
        letter-spacing: 1px;

        padding: applyMath(15,0,$pc,$tablet) applyMath(15,0,$pc,$tablet);
        font-size: applyMath(16,8,$pc,$tablet);
    }

    input , button {
        @include media("<=tablet",">min-width"){
            height: applyMath(35,20,$tablet,320);
            width: applyMath(425,250,$tablet,320);
            align-self: center;
        } 
        @include media("<=min-width") {
            height: 20px;
            width: 250px;
            align-self: center;
        }
    }

}
</style>
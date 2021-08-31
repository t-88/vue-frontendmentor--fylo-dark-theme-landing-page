<template>
    <button>{{ text }}</button>
</template>

<script>
export default {
    name: "Button",
    props: {
        text: { type: String, default: "" },
    },
}
</script>

<style lang="scss" scoped>
    button {
        color: white;
        font-weight: 700;
        font-size: 14px;
        border: transparent;
        background: linear-gradient(to right, #65e2d9, #339ecc);
        padding: 15px 55px;
        border-radius: 200px;
        cursor: pointer;

        &:hover {
            background: #65e2d9;
        }
    }
</style>
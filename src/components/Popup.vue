<template>
    <div class="popup">
        <h3 class="popup__title" v-if="title !== ''">{{ title }}</h3>
        <slot></slot>
    </div>
</template>

<script>
    export default {
        name: "Popup",
        props: {
            title: {
                type: String,
                default: '',
                required: false
            }
        }
    }
</script>

<style scoped>

    .popup {
        position: absolute;
        width: 500px;
        max-width: 100%;
        left: 50%;
        top: 50%;
        -webkit-transform: translate(-50%, -50%);
        -moz-transform: translate(-50%, -50%);
        -ms-transform: translate(-50%, -50%);
        -o-transform: translate(-50%, -50%);
        transform: translate(-50%, -50%);
        padding: 2rem;
        background: #eaeaea;
        -webkit-border-radius: 5px;
        -moz-border-radius: 5px;
        border-radius: 5px;
    }

    .popup__title {
        margin-bottom: 1.5rem;
    }

</style>
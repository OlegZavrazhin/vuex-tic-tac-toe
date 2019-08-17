<template>

    <svg class="circle" height="105" width="105" viewBox="0 0 105 105">
        <circle
                class="circle-component"
                cx="52.5" cy="52.5" r="50"
                stroke="rgb(0,0,0)"
                stroke-width="5"
                fill="none"
                preserveAspectRatio="xMinYMin meet"/>
    </svg>

</template>

<script>
    export default {
        name: "CircleComponent"
    }
</script>

<style scoped>

    .circle {
        max-width: calc(100% - 5px);
    }

    .circle-component {
        stroke-dasharray: 1000;
        stroke-dashoffset: 1000;
        animation: drawCircleComponent 3s linear forwards;
    }

    @keyframes drawCircleComponent {
        to {
            stroke-dashoffset: 0;
        }
    }

</style>
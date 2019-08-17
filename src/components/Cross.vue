<template>

    <svg class="cross" height="100" width="100" viewBox="0 0 100 100">
        <line class="cross__line cross__line_first" x1="0" y1="0" x2="100" y2="100" style="stroke:rgb(0,0,0);stroke-width:5" preserveAspectRatio="xMinYMin meet" />
        <line class="cross__line cross__line_second" x1="100" y1="0" x2="0" y2="100" style="stroke:rgb(0,0,0);stroke-width:5" preserveAspectRatio="xMinYMin meet" />
    </svg>

</template>

<script>
    export default {
        name: "Cross"
    }
</script>

<style scoped>

    .cross {
        max-width: calc(100% - 5px);
    }

    .cross__line {
        stroke-dasharray: 1000;
        stroke-dashoffset: 1000;
        animation: drawCross 3s linear forwards;
    }

    @keyframes drawCross {

        to {
            stroke-dashoffset: 0;
        }

    }

    /*.cross__line_first {*/

    /*}*/

    /*.cross__line_second {*/

    /*}*/

</style>
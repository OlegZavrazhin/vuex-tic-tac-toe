<template>
    <div class="container">
        <div class="row center-xs">
            <div class="col-xs-12 col-md-8 col-lg-6">
                <div class="box">
                    <Wrapper/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    // @ is an alias to /src
    import Wrapper from '@/components/Wrapper';

    export default {
        name: 'home',
        components: {
            Wrapper
        }
    }
</script>

<template>

    <div class="container">
        <div class="row">
            <div class="col-xs-12">
                <button class="btn btn-primary game-detail__btn"
                        type="button"
                        @click="$router.go(-1)">
                    Back
                </button>
            </div>
        </div>
        <div class="row center-xs">
            <div class="col-xs-12 col-md-8 col-lg-6">
                <div class="box">
                    <WrapperTable :route-id="+$route.params.id"/>
                </div>
            </div>
        </div>
    </div>

    
</template>

<script>
    import WrapperTable from '@/components/WrapperTable';

    export default {
        name: 'GameDetail',
        components: {
            WrapperTable
        },
        created() {
            // console.log('this.$route.params.id', this.$route.params.id);
        }
    }
</script>

<style scoped>

    .game-detail__btn {
        margin: 1.5rem 0;
    }

</style>
<template>

    <div class="wrapper__table-wrap">

        <table
                class="wrapper__table"
                :class="{'wrapper__table_no_clicks': currentGame.done || !currentGame.turn}"
                @click="setPlayerSign(currentGame.turn, $event)"
        >
            <tr v-for="(row, rowKey) in currentGame.rows"
                :key="rowKey"
                class="wrapper__row">
                <td v-for="(cell, cellKey) in row.cells"
                    :key="cellKey"
                    class="wrapper__cell">
                    <Cross v-if="cell.value === 'cross'"/>
                    <CircleComponent v-if="cell.value === 'circle'" />
                </td>
            </tr>
        </table>

        <Popup v-if="!currentGame.turn" title="Start A New Game?">
            <div class="row center-xs">
                <div class="col-xs-12 col-md-6">
                    <button class="btn btn-primary wrapper__btn wrapper__btn_first"
                            type="button"
                            @click="chooseTurn('circle')">
                        Start with circles
                    </button>
                </div>
                <div class="col-xs-12 col-md-6">
                    <button
                            class="btn btn-primary wrapper__btn"
                            type="button"
                            @click="chooseTurn('cross')">
                        Start with crosses
                    </button>
                </div>
            </div>
        </Popup>

    </div>

</template>

<script>
    import { mapGetters, mapActions } from 'vuex';

    import Cross from './Cross';
    import CircleComponent from './CircleComponent';
    import Popup from './Popup';

    export default {
        name: 'WrapperTable',
        components: {
            Cross,
            CircleComponent,
            Popup,
        },
        props: {
            routeId: {
                type: Number,
                default: 0,
                required: false,
                validator: (value) => {
                    return typeof value === 'number';
                }
            }
        },
        computed: {
            ...mapGetters(['currentGameState']),
            currentGame() {
                if (!this.routeId) {
                    return this.currentGameState();
                } else {
                    return this.currentGameState(this.routeId);
                }
            }
        },
        methods: {
            ...mapActions([
                'changeTurnAndValue',
                'checkWinner',
                'chooseTurn',
                'prepareGameData'
            ]),
            async setPlayerSign(turn, event) {

                const target = event.target;


                const rowIndex = target.closest('tr').rowIndex;
                const cellIndex = target.cellIndex;

                await this.changeTurnAndValue({turn, rowIndex, cellIndex});

                this.checkWinner({turn, rowIndex, cellIndex});

            }
        },
        created() {
            if (this.currentGame.rows.length === 0) {
                this.prepareGameData();
            }
        }
    }
</script>

<style scoped>

    .wrapper__table {
        width: 100%;
        border-collapse: collapse;
    }

    .wrapper__cell {
        height: 10.45rem;
        border: 1px solid #eaeaea;
        width: 33.33%;
    }

    .wrapper__table_no_clicks {
        pointer-events: none;
        background: rgba(234,234,234,0.7);
    }

    .wrapper__table-wrap {
        position: relative;
    }

</style>
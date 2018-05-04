<script type="text/ecmascript-6">
    import _ from 'lodash';
    import moment from 'moment';
    import Layout from '../../layouts/MainLayout.vue';

    export default {
        props: ['slug'],


        components: {Layout},


        /**
         * The component's data.
         */
        data() {
            return {
                loading: true,
                rawData: {},
                metric: {}
            };
        },


        /**
         * Prepare the component.
         */
        mounted() {
            this.loadMetric();
        },


        methods: {
            /**
             * Load the metric.
             */
            loadMetric() {
                this.loading = true;

                this.$http.get('/horizon/api/queue/' + encodeURIComponent(this.slug))
                    .then(response => {
                        let data = this.prepareData(response.data);

                        this.rawData = response.data;

                        // this.metric.throughPutChart = this.buildChartData(data, 'throughput', 'Times');

                        // this.metric.runTimeChart = this.buildChartData(data, 'runtime', 'Seconds');

                        this.loading = false;
                    });
            },
        }
    };
</script>

<template>
    <layout>
        <section class="main-content">
            <div class="card mb-4">
                <div class="card-header">{{slug}}</div>
                <div class="card-body">


                    <p class="text-center m-0 p-5">
                        TEST TOM
                    </p>

                </div>
            </div>
        </section>
    </layout>
</template>

<template>
    <detail :resource="orderVariation"
        class="mb-10" />
</template>

<script>
    import Detail from 'Vendor/js/components/Templates/Detail'
    import {Index} from 'Vendor/js/components/Templates/Index'
    import ResourceDetail from 'Vendor/js/Mixins/ResourceDetail'

    export default {
        components: {
            Detail,
            Index
        },
        mixins: [ResourceDetail],
        data() {
            return {
                orderVariation: {},
                resource: 'orderVariation'
            }
        },
        async created() {
            const { data } = await Admin.request('order-variations').detail(this.$route.params.id)

            this.orderVariation = data
        }
    }
</script>

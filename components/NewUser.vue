<template>
    <div>
        <div v-for="items in dataarray" :key="items">
        <!-- {{data.Name}} -->
        <User v-bind:dataarray="dataarray" v-bind:items="items"></User>
        </div>
    </div>
</template>
<script>
import User from '/components/User.vue'
export default {
    name: "New User",
    props: ['dataarray'],
    components:{User}
}
</script>
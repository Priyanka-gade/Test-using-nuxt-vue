<template>
    <div>
        <div v-for="data in dataarray" :key="data">
        {{data.Name}}
        <User></User>
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
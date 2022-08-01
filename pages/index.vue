<template>
    
    <h1>Hello</h1>
    <Table></Table>
    <NewUser></NewUser>
</template>
<script>

import Table from '/components/Table.vue'
import NewUser from '/components/NewUser.vue'

export default {
    name: "index component",
    components: {Table,NewUser }
}
</script>
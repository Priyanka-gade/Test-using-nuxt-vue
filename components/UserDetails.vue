<template>
    <div>
        <div v-for="items in dataarray" :key="items.id">
            {{ items.Name }}
        </div>
    </div>
</template>
<script>
export default {
    name: "UserC",
    props: ['dataarray']

}
</script>
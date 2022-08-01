<template>
    <div v-for="items in dataarray" :key="items">
    {{items.Name}}
    </div>
</template>
<script>
export default {
    name: "UserC",
    props:['dataarray']
    
}
</script>
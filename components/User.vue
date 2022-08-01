<template>
    <div class="flex flex-col items-center ">
        <div class="m-2 p-2 bg-slate-200 w-64 ">
                <p>{{ items.Name }}</p>
                <p>{{ items.Email }}</p>
                <p>{{ items.Mobile }}</p>
                <p>{{ items.Address }}</p>
                <button 
                    class="del font-serif font-semibold float-right bg-red-500 rounded-md text-white p-1 m-1">Delete</button>
                <button 
                    class="font-serif font-semibold float-right bg-green-800 rounded-md text-white p-1 m-1">Edit</button>
        </div>
    </div>
</template>
<script>
export default {
    name: "UserC",
    props:['dataarray']
}
</script>
<template>
    <div class="grid justify-items-center">
        <div>
                <button @click="add" class=" bg-blue-700 border-1 border-black text-white p-1 rounded-md font-serif font-semibold ">
                    Add </button>
            </div>
            <div>
                <form class="grid justify-items-left bg-slate-200 p-7 w-64">
            <h1 class="text-center">Add New user </h1>
            <div>
                <input type="text" placeholder="Name" required />{{ items.Name }}
            </div><br />
            <div>
                <input type="text" placeholder="Email" required />{{ items.Email }}
            </div><br />
            <div>
                <input type="text" placeholder="Mobile" required />{{ items.Mobile }}
            </div><br />
            <div>
                <input type="text" placeholder="Address" required />{{ items.Address }}
            </div><br />
            <br />
        </form>
            </div>
    </div>
</template>
<script>
export default {
    name: "UserC",
    props: [ 'dataarray','items']

}
</script>
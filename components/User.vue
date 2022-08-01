<template>
    <div class="grid justify-items-center">
        <form class="grid justify-items-left bg-slate-200 p-7 w-64">
            <h1 class="text-center">Add New user </h1>
            <div>
                <input type="text" placeholder="Name" required />
            </div><br/>
            <div>
                <input type="text" placeholder="Email" required />
            </div><br/>
            <div>
                <input type="text" placeholder="Mobile" required />
            </div><br/>
            <div>
                <input type="text" placeholder="Address" required />
            </div><br/>
            <br />
            <div>
                <button class=" bg-blue-700 border-1 border-black text-white p-1 rounded-md font-serif font-semibold ">
                    Add </button>
            </div>
        </form>
    </div>
</template>
<script>
export default{
    name:"UserC"
}
</script>
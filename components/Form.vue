<template>
    <div class="sm:grid justify-items-center">
        <div>
            <form class="grid justify-items-left bg-slate-200 p-7 w-64">
                <h1 class="text-center">Add New user </h1>
                <div>
                    <input type="text" placeholder="Name" required />
                </div><br />
                <div>
                    <input type="text" placeholder="Email" required />
                </div><br />
                <div>
                    <input type="text" placeholder="Mobile" required />
                </div><br />
                <div>
                    <input type="text" placeholder="Address" required />
                </div><br />
                <br />
                <button class="border rounded-lg p-1 bg-blue-600 text-white">Add User</button>
            </form>
        </div>
    </div>
</template>
<script>

export default {
    name: "User Form",


}
</script>
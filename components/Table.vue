<template>
    <div>
        <table class="m-10 justify-center border border-solid border-2 border-black">
            <tr class="border border-solid border-black">
                <th class="py-3 px-6">
                    Name
                </th>
                <th class="py-3 px-6">
                    Email
                </th>
                <th class="py-3 px-6">
                    Mobile
                </th>
                <th class="py-3 px-6">
                    Address
                </th>
                <th class="py-3 px-6">
                    Actions
                </th>
            </tr>
            <!-- <tr>
                <td>Priyanka</td>
                <td>Pg@gmail.com</td>
                <td>9922498956</td>
                <td>Pollard Farms Baner</td>
                <td colspan="2"><button class="border rounded-lg p-1 bg-blue-600 text-white">Edit</button>&nbsp;<button
                        class="border rounded-lg p-1 bg-red-500 text-white">Delete</button></td>
            </tr> -->
        </table>
        <button class="border rounded-lg p-1 bg-blue-600 text-white">Add User</button>
        
    </div>
</template>
<script>


export default {
    name: 'Table Component',
    data() {
        return {
            dataarray: [
                {
                    id: '1',
                    Name: "Priyanka",
                    Email: "pg@gmail.com",
                    Mobile: "9922498956",
                    Address: "Pollard Farms Baner1",
                    // completed:false
                },
                {
                    id: '2',
                    Name: "Amita",
                    Email: "ak@gmail.com",
                    Mobile: "9765568956",
                    Address: "Pollard Farms Baner2",
                    // completed: false
                }
            ]
    }
}
}
</script>
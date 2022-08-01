<template>
    <div>
        <table class="sm:flex justify-center border-b m-2">
            <tr class="sm:flex bg-slate-200">
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
            <tr>
                <td>P</td>
                <td>Pg@gmail.com</td>
                <td>9922498956</td>
                <td>Pollard Farms Baner</td>
                <td colspan="2"><button class="border rounded-lg p-1 bg-blue-600 text-white">Edit</button>&nbsp;<button
                        class="border rounded-lg p-1 bg-red-500 text-white">Delete</button></td>
            </tr>
            <!-- <tr>
                <td colspan="5"><button class=" float-right border rounded-lg p-1 bg-blue-600 text-white">Add User</button></td>
            </tr> -->
        </table>
        <UserDetails></UserDetails>
        <!-- <button class="border rounded-lg p-1 bg-blue-600 text-white">Add User</button> -->
    </div>
</template>
<script>

import UserDetails from '/components/UserDetails.vue'
export default {
    name: 'Table Component',
    props:['dataarray'],
    components:{UserDetails}
    
   
}
</script>
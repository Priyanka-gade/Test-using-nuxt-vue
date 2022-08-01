<template>
    <div class="sm:grid justify-items-center">
        <div>
            <form class="grid justify-items-left bg-slate-200 p-7 w-64">
                <h1 class="text-center">Add New user </h1>
                <div>
                    <input type="text" v-model="Name" placeholder="Name" required />
                </div><br />
                <div>
                    <input type="text" v-model="Email" placeholder="Email" required />
                </div><br />
                <div>
                    <input type="text" v-model="Mobile" placeholder="Mobile" required />
                </div><br />
                <div>
                    <input type="text" v-model="Address" placeholder="Address" required />
                </div><br />
                <br />
                <button @click="adduser" class="border rounded-lg p-1 bg-blue-600 text-white">Add User</button>
            </form>
        </div>
        <div>
            <table class="sm:flex justify-center border-b m-2">
            <tr class="sm:flex bg-slat)e-200">
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
             <tr>
                <td>{{this.Name}}</td>
                <td>{{this.Email}}</td>
                <td>{{this.Mobile}}</td>
                <td>{{this.Address}}</td>
                <td colspan="2"><button class="border rounded-lg p-1 bg-blue-600 text-white">Edit</button>&nbsp;<button
                        class="border rounded-lg p-1 bg-red-500 text-white">Delete</button></td>
            </tr>
        </table>
        </div>
    </div>
</template>
<script>

import  UserDetails  from '/components/UserDetails.vue'
export default {
    name: "User Form",
    components:{UserDetails},
    props:['dataarray','items'],
// methods:{
//     adduser(){
//         this.dataarray.push(this.user)
//     }
// }
data(){
    return{
        Name:'',
        Email:'',
        Mobile:'',
        Address:''
    }
}
}
</script>
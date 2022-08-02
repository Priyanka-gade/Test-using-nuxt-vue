<template>
    <div class="">
        <div class="float-left">
            <form class="sm:grid justify-items-left bg-slate-200 p-7 ">
                <h1 class="text-center">Add New user </h1>
                <div>
                    <input type="text" class="capitalize" @keyup="userFndName(newUser.Name)" v-model="newUser.Name" placeholder="Name" required />
                </div><br />
                <div>
                    <input type="text" @keyup="userFndEmail(newUser.Email)" v-model="newUser.Email" placeholder="Email" required />
                </div><br />
                <div>
                    <input type="text" @keyup="userFndMobile(newUser.Mobile)" v-model="newUser.Mobile" placeholder="Mobile" required />
                </div><br />
                <div>
                    <textarea type="text" @keyup="userFndAddress(newUser.Address)" v-model="newUser.Address" placeholder="Address" class="w-52" required />
                </div><br />
                <br />
                <button id="btnadd" @click="addUserTodata" type="button" class="border rounded-lg p-1 bg-blue-600 text-white">Add
                    User</button>
                <!-- <button type="reset">Reset</button> -->
            </form>
        </div>
        <div class="sm:float-right bg-slate-200 w-2/3">
            <div class="bg-slate-200 sm:float-right p-2">
                <input type="search" class="rounded-full bg-white p-1" placeholder="Search" />
            </div>
            <table class="border">
                <tr class="bg-slate-200 border my-2">
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
                <!-- <tr class="sm:flex bg-slate-100 border-b border-2">
                    <td>P</td>
                    <td>Pg@gmail.com</td>
                    <td>9922498956</td>
                    <td>Pollard Farms Baner</td>
                    <td colspan="2"><button
                            class="border rounded-lg p-1 bg-blue-600 text-white">Edit</button>&nbsp;<button
                            class="border rounded-lg p-1 bg-red-500 text-white">Delete</button></td>
                </tr> -->
                <tr v-for="(row, i) in dataarray" :key="row" class=" bg-slate-100 border-b">
                    <td>{{ row.Name }}</td>
                    <td>{{ row.Email }}</td>
                    <td>{{ row.Mobile }}</td>
                    <td>{{ row.Address }}</td>
                    <td colspan="2"><button @click="editUserDetails(i)"
                            class="border rounded-lg p-1 bg-blue-600 text-white">Edit</button>&nbsp;
                        <button @click="deleteUser(i)"
                            class="border rounded-lg p-1 bg-red-500 text-white">Delete</button>
                    </td>
                </tr>
            </table>
        </div>
        <!-- <div v-if="this.flag" class="flex flex-row">
            <form @submit="updatedata()" class="grid justify-items-left bg-slate-200 p-7 w-64">
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
                <button type="button" class="border rounded-lg p-1 bg-blue-600 text-white">
                    Update</button>
            </form> 
        </div>-->
    </div>
</template>
<script>

import UserDetails from '/components/UserDetails.vue'
export default {
    name: "User Form",
    components: { UserDetails },
    props: ['dataarray', 'items'],
    data() {
        return {
            isEdit: false,
            editIndex: -1,
            newUser: {
                Name: null,
                Email: '',
                Mobile: '',
                Address: ''
            },

            flag: false,

            userFINd: [],
            uniqueEmail:[],
        }
    },
    methods: {
        addUserTodata(e) {
            e.preventDefault()
            // const newUser = {
            //     id: Date.now(),
            //     Name: this.Name,
            //     Email: this.Email,
            //     Mobile: this.Mobile,
            //     Address: this.Address
            // }
            if (this.isEdit === true) {
                this.dataarray[this.editIndex] = this.newUser;
                (this.isEdit = false), (this.editIndex = -1);
                 let updatebtn= document.getElementById("btnadd");
                 updatebtn.innerText="Add User";
            } else {
                this.dataarray.push(this.newUser);
            }


            this.newUser = {
                Name: '',
                Email: '',
                Mobile: '',
                Address: ''
            }


        },
        deleteUser(index) {
            this.dataarray.splice(index, 1);
        },
        editUserDetails(i) {
            this.flag = !this.flag

            this.newUser.id = this.dataarray[i].id;
            this.newUser.Name = this.dataarray[i].Name;
            this.newUser.Email = this.dataarray[i].Email;
            this.newUser.Mobile = this.dataarray[i].Mobile;
            this.isEdit = true;
            this.editIndex = i;
            let updatebtn= document.getElementById("btnadd");
                 updatebtn.innerText="Update";
        },
        updatedata(e) {
            e.preventDefault()
            //  this.newUser.id = this.dataarray[i].id
            // this.newUser.Name = this.dataarray[i].Name;
            // this.newUser.Email = this.dataarray[i].Email;
            // this.newUser.Mobile = this.dataarray[i].Mobile;
            // this.dataarray.filter((items) => {
            //     if (items.id == this.id) {
            //         items.Name = this.Name,
            //         items.Email= this.Email,
            //         items.Mobile=this.Mobile,
            //         items.Address=this.Address
            //     }
            // })
        },
        userFindByName(){
            // console.log(newUser.Name);
            this.userFind = this.dataarray.filter((e) => {
                
                if(e.Name.startsWith(newUser.Name)){
                    console.log(e);
                    return e;
                }
            });
            console.log(this.userFind);
        },
    }

}

</script>
<template>
    <div class="sm:grid gap-x-7 grid-cols-3 h-screen bg-red-300 w-3/4 m-5">
        <div class="border border-solid border-2 border-slate-400">
            <form class="sm:justify-items-center font-bold bg-slate-300 p-4 ">
                <br />
                <h1 id="title" class="text-center text-xl font-bold font-serif">Add New user </h1>
                <div class="m-5 items-center p-2 ">
                    <br />
                    <div>
                        <label>Name :</label><br />
                        <input type="text" class="sm:capitalize w-52 p-2 rounded-lg" v-model="newUser.Name"
                            placeholder="Name" required />
                    </div><br />
                    <div>
                        <label>Email :</label><br />
                        <input type="text" v-model="newUser.Email" class=" sm:w-52 p-2 rounded-lg" title="incorrect email"
                            placeholder="abc@gmail.com" required />
                    </div><br />
                    <div>
                        <label>Mobile :</label><br />
                        <input type="text" class="sm:w-52 p-2 rounded-lg" v-model="newUser.Mobile"
                            placeholder="Mobile +91XXXXXXXXXX" required />
                    </div><br />
                    <div>
                        <label>Address :</label><br />
                        <textarea type="text" class=" sm:w-52 p-2 rounded-lg" v-model="newUser.Address"
                            placeholder="Address" required></textarea>
                    </div><br />
                    <br />
                    <button id="btnadd" @click="addUserTodata" type="button"
                        class="sm:border rounded-lg p-1 bg-gradient-to-r from-green-400 to-blue-500 hover:from-pink-500 hover:to-yellow-500 text-white">Add
                        User</button>&nbsp;
                    <button id="btnadd" @click="resetTodata" type="button"
                        class="sm:border rounded-lg p-1 bg-gradient-to-r from-green-400 to-blue-500 hover:from-pink-500 hover:to-yellow-500 text-white">
                        Reset</button>
                    <br />
                </div>
                <!-- <button type="reset">Reset</button> -->
            </form>
        </div>
        <div class="sm:float-right bg-slate-300 border border-solid border-2 border-slate-400 col-span-2 p-1 w-full">
            <div class="bg-slate-200 sm:float-right p-2 ">
                <input type="search" @input="searchInput($event)" class="sm:rounded-full bg-white p-1"
                    placeholder="Search" />
            </div>
            <br/>
            <table class="sm:border w-full auto-cols-max col-span-2">
                <!-- {{stordata}} -->
                <tr class="sm:bg-slate-400 border my-2 ">
                    <th class="sm:py-3 px-6">
                        Name
                    </th>
                    <th class="sm:py-3 px-6">
                        Email
                    </th>
                    <th class="sm:py-3 px-6">
                        Mobile
                    </th>
                    <th class="sm:py-3 px-6">
                        Address
                    </th>
                    <th class="sm:py-3 px-6">
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

                <tr v-for="(row, i) in filterRecords" :key="row" class=" sm:bg-white border-b border-slate-300">
                    <td class="sm:py-3 px-6">{{ row.Name }}</td>
                    <td class="sm:py-3 px-6"><a href="#" class="underline-offset-4 text-blue-600" >{{ row.Email }}</a></td>
                    <td class="sm:py-3 px-6">{{ row.Mobile }}</td>
                    <td class="sm:py-3 px-6">{{ row.Address }}</td>
                    <td colspan="2" class="sm:py-3 px-6"><button @click="editUserDetails(i)"
                            class="sm:border rounded-lg p-1 bg-gradient-to-r from-blue-400 to-blue-900 text-white">Edit</button>&nbsp;
                        <button @click="deleteUser(i)"
                            class="sm:border rounded-lg p-1 bg-gradient-to-r from-red-400 to-red-900 text-white">Delete</button>
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
            edtIndex: -1,
            newUser: {
                Name: null,
                Email: '',
                Mobile: '',
                Address: ''
            },
            searchText: '',

            flag: false,
            checkemail: ''
        }
    },
    computed: {
        stordata() {
            this.dataarray = JSON.parse(localStorage.getItem("user"))

        },
        filterRecords() {
            if (this.searchText) {
                return this.dataarray.filter(user => user.Name.toLowerCase().includes(this.searchText.toLowerCase()))
            }
            return this.dataarray;
        }
    },
    methods: {
        addUserTodata(e) {
            e.preventDefault()
            this.checkemail = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/;
            this.checkmobile = /^[+][(]?[0-9]{1,3}[)]?[-\s.]?[0-9]{3}[-\s.]?[0-9]{4,7}$/gm;
            // const newUser = {
            //     id: Date.now(),
            //     Name: this.Name,
            //     Email: this.Email,
            //     Mobile: this.Mobile,
            //     Address: this.Address
            // }

            if (this.isEdit === true) {
                this.dataarray[this.edtIndex] = this.newUser;
                (this.isEdit = false), (this.edtIndex = -1);
                let updatebtn = document.getElementById("btnadd");
                let formtitle = document.getElementById("title");
                updatebtn.innerText = "Add User";
                formtitle.innerText = "Update User";
            }
            else if (!isNaN(this.newUser.Name) || this.newUser.Name == null || this.newUser.Name == "") {
                alert("Please Enter Name");
            }
            // else if (this.checkemail.test(this.newUser.Email)) {
            // ||dataarray.Email==newUser.Email
            // }
            else if (!this.checkemail.test(this.newUser.Email)) {
                alert("Email is Invalid");
            }
            // else if (this.dataarray.Email == this.newUser.Email) {
            //     alert("Email is already added");
            // }
            else if (!this.checkmobile.test(this.newUser.Mobile)) {
                alert("mob is Invalid");
            }
            // else if (!this.checkmobile.test(this.newUser.Mobile)) {
            //     alert("Mobile no. is Invalid");
            // }
            else if (this.newUser.Address == null || this.newUser.Address == "") {
                alert("Please Enter Address");
            }
            else {
                this.dataarray.push(this.newUser);
            }
            this.newUser = {
                Name: '',
                Email: '',
                Mobile: '',
                Address: ''
            },
                localStorage.setItem("user", JSON.stringify(this.dataarray))
        },
        searchInput(e) {
            this.searchText = e.target.value;
            console.log(e.target.value)
        },
        deleteUser(index) {
            this.dataarray.splice(index, 1);

            // updatebtn = document.getElementById("btnadd");
            // formtitle = document.getElementById("title");
            // updatebtn.innerText = "Add";
            // formtitle.innerText = "Add User";
        },
        editUserDetails(i) {
            // this.flag = !this.flag

            // this.newUser.id = this.dataarray[i].id;
            this.newUser.Name = this.dataarray[i].Name;
            this.newUser.Email = this.dataarray[i].Email;
            this.newUser.Mobile = this.dataarray[i].Mobile;
            this.newUser.Address = this.dataarray[i].Address;
            this.isEdit = true;
            this.edtIndex = i;
            let updatebtn = document.getElementById("btnadd");
            let formtitle = document.getElementById("title");
            updatebtn.innerText = "Update";
            formtitle.innerText = "Update User";
        },
        resetTodata() {
            this.isEdit = false;
            this.edtIndex = -1;
            this.newUser = {
                Name: null,
                Email: '',
                Mobile: '',
                Address: ''
            },
            updatebtn = document.getElementById("btnadd");
            formtitle = document.getElementById("title");
            updatebtn.innerText = "Submit";
            formtitle.innerText = "Add User";
        }
        // updatedata(e) {
        //     e.preventDefault()
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
        // }
    }
}

</script>
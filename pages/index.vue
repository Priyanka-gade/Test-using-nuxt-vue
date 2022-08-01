<template>
    <div class="sm:flex w-2/3 p-5 m-5">
        <Form v-bind:dataarray="dataarray" v-on:add-user="addUserTodata" class="float-left"></Form>
        <!-- <Table v-bind:dataarray="dataarray" class="float-right"></Table> -->

    </div>
</template>
<script>

// import Table from '/components/Table.vue'
import Form from '/components/Form.vue'


export default {
    name: "index component",
    components: { Form },
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
        },
        methods:{
            addUserTodata(newUser){
                this.dataarray=[...this.dataarray,newUser]
                // console.log(this.addUserTodata);
            }
        }
}
</script>
<template>
    <div>
     <h1> Delete Data With API</h1>

     <table>
        <tr>
            <td>Name</td>
            <td>Username</td>
            <td>Email</td>
            <td>Address</td>
            <td>Action</td>
        </tr>
        <tr v-for="user in users" v-bind:key="user.id">
            <td>{{user.name}}</td>
            <td>{{user.username}}</td>
            <td>{{user.email}}</td>
            <td>{{user.address.city}}</td>
            <td><button v-on:click ="deleteUser(user.id)">Delete</button> </td>
        </tr>
     </table>
    </div>
</template>
<script>

import  Vue from 'vue';
import VueAxios from 'vue-axios';
import axios from 'axios'

Vue.use(VueAxios,axios)

export default{
    name : 'UserCom',
     data(){
        return{
             users:null
        }
     },
     methods:{
         getUsers()
{
         this.axios.get('https://jsonplaceholder.typicode.com/users').then((result)=>{
            this.users = result.data
             console.log(result)
        })

       
},
 deleteUser(id){
            this.axios.delete('https://jsonplaceholder.typicode.com/users/'+id).then((result)=>{
           
                console.log(result)
                 
                this.getUsers( )
            })

        }  

},
     mounted(){
        this.getUsers();
     }

}


</script>
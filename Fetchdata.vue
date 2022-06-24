<template>
    <div>
  <h2>fetch Data with API</h2>
  <table>
    <tr>
        <td>Name</td>
        <td>Username</td>
        <td>Address</td>
        <td>Email</td>
        <td>Company</td>
    </tr>
    <tr v-for="item in list" v-bind:key="item.id">
        <td>{{item.name}}</td>
        <td>{{item.username}}</td>
        <td>{{item.address}}</td>
        <td>{{item.email}}</td>
        <td>{{item.company}}</td>
    </tr>
  </table>


    </div>
</template>

<script>

import  Vue from 'vue';
import VueAxios from 'vue-axios';
import axios from 'axios'

Vue.use(VueAxios,axios)
export default {
    name : 'FetchData',

    data(){
      return {
        list: undefined
      }
    },

    mounted(){
        Vue.axios.get('https://jsonplaceholder.typicode.com/users')
        .then(resp =>{
            this.list = resp.data;
            console.log(resp.data)
        })
    }

}


</script>
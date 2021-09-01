<template>
  <div>
    <div class="container text-center">
      <h1>Fetch The Data With API</h1>

    <table class="table table-bordered">
      <thead>
        <tr>
          <th scope="col">ID</th>
          <th scope="col">Email</th>
          <th scope="col">First Nmae</th>
          <th scope="col">Last Name</th>
          <th scope="col">Image</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in list" v-bind:key="item.id">
          <td>{{item.id}}</td>
          <th>{{item.email}}</th>
          <td>{{item.first_name}}</td>
          <td>{{item.last_name}}</td>
          <td><img :src="item.avatar" alt=""></td>
       </tr>
      </tbody>
    </table>
    </div>
  </div>
</template>

<script>

import Vue from 'vue';
import axios from 'axios';
import VueAxios from 'vue-axios';
Vue.use(VueAxios,axios)


export default {
  name: 'home',
  props: {
    msg: String
  },

  data(){
    return{
      list:undefined
    }
  },

  mounted(){
    Vue.axios.get('https://reqres.in/api/users?page=2')
    .then(res=>{
      this.list = res.data.data 
      // console.log(res.data.data)
    })
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

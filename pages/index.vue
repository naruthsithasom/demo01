<template>
<div>
  <h1>Home</h1>
  <input type="text" v-model="name" />
  <br>
  <button @click="onClickSubmit(1)">UP</button>
  <button @click="onClickSubmit(-1)">Down</button>
  <br>
  <button @click="onClickReset" >Reset</button>
  <p>{{name}}</p><br>
  <h1>{{temp}}</h1>
  <hr>
  <table>
    <th>
      <td>id</td>
      <td>text</td>
    </th>
    <!-- v-for -->
    <!-- v-if -->
    <tr v-for="data in datataTable" :key="data.id">
      <td v-if="data.id %2 == 0">{{data.id}}</td>
      <td>{{ text }}</td>
    </tr>
  </table>
  <hr>
  <!-- @click -->
  <!-- :class -->

</div>
</template>

<script>
export default {
layout:"default",
data(){
  return{
    name:"",
    id:[],
    obj:{},
    temp:0,
    datataTable:[
      {id: 1 , text: "hello wolrd1"},
      {id: 2 , text: "hello wolrd2"},
      {id: 3 , text: "hello wolrd3"},
      {id: 4 , text: "number4"},
    ],
    isDisabled:false,
    color: "",
  }
},
mounted(){

},
computed:{},
methods:{
  onClickSubmit(data){
    this.temp += data
  },
   onClickReset(data){
   this.temp = 0
  },
  onClockSwColor(data){
    this.isDisabled = !this.isDisabled
    this.color = data
  }
},
}
</script>

<style>
.red{
  background-color: red;
}
.green{
  background-color: green;
}
.blue{
  background-color: blue;
}
</style>

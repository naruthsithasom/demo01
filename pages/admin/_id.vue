<template>
  <div>
    <h1>Params</h1>
    <h1> {{ name }} : {{$route.params.id}}</h1>
  </div>
</template>
<script>
export default {
  data(){
    return{
      name:"Admin"
    }
  }
}
</script>
<style>

</style>
<template>
  <table class="table">
  <thead>
    <tr>
      <th scope="col">Sort</th>
      <th scope="col">Job title</th>
      <th scope="col">Level</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">1</th>
      <td>Mark</td>
      <td>Otto</td>
      <td>@mdo</td>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>Jacob</td>
      <td>Thornton</td>
      <td>@fat</td>
    </tr>
    <tr>
      <th scope="row">3</th>
      <td>Larry</td>
      <td>the Bird</td>
      <td>@twitter</td>
    </tr>
  </tbody>
</table>
</template>
<script>
export default {
  data(){
    return{

    }
  },
  mounted(){
    this.$axios.$post('/api/page/jobs').then( res => {
      if(res){
        console.log(res)
      }
    }).catch( error => console.log(error))
  }
}
</script>
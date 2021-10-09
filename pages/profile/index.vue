<template>
  <div>
    <form @submit="onClickSubmit" @reset="onClickReset">
      <b-form-input v-model="name" placeholder="Enter your name"></b-form-input>
      <b-form-input v-model="sid" placeholder="Enter your sid"></b-form-input>
      <b-button type="reset" variant="danger">RESET</b-button>
      <b-button type="submit" variant="success">OK</b-button>
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: '',
      sid: 0,
    }
  },
  methods:{
    onClickSubmit(e){
      e.preventDefault()
      console.log('name'+this.name +', sid:' + this.sid)
      this.$router.push('/profile/'+this.sid)
      // this.$router.push({path:'/profile', params: {sid: this.sid}})
    },
    onClickReset(){
      
    }
  }
}
</script>
<style>
</style>
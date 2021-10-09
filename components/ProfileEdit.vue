<template>
      <!-- 
      ref="modal"
      title="Submit Your Name"
      @show="resetModal"
      @hidden="resetModal"
      @ok="handleOk" -->
     <b-modal
        id="ProfileEdit"
        hide-footer
    >
      <!-- <form ref="form" @submit.stop.prevent="handleSubmit"> -->
      <form ref="form" >
        <!-- {{dataEdit}} -->
        <b-form-group
          :label="`${dataEdit.name} sid: ${dataEdit.sid}`"
          label-for="name-input"
          invalid-feedback="Name is required"
          :state="nameState"
        >
          <b-form-input
            id="name-input"
            v-model="dataEdit.name"
            :state="nameState"
            required
          ></b-form-input>
          <br>
          <b-form-input
            id="name-input"
            v-model="dataEdit.sid"
            :state="idState"
            required
          ></b-form-input>
          <br>
          <b-form-input
            id="name-input"
            v-model="dataEdit.img"
            :state="imgState"
            required
          ></b-form-input>
        </b-form-group>
        <button @click="onClickDataEdit" type="submit" class="btn primary">OK</button>
      </form>
    </b-modal>
</template>
<script>
export default {
  props:['dataEdit'],
  data(){
    return{
      name:"",
      form:{
        name:"",
        sid:0,
        img:""
      },
    }
  },
  mounted(){
    //  this.form = [...this.dataEdit]
    //  this.name = this.dataEdit.name
  },
  computed:{
   nameState(){
    if(this.dataEdit.name != null){
      if(this.dataEdit.name.length > 5){
        return true
      } else {
        return false
      }
    }
   },
   idState(){
    if(this.dataEdit.sid != null){
      if(this.dataEdit.sid > 0){
        return true
      } else {
        return false
      }
    }
   },
   imgState(){
    if(this.dataEdit.img != null){
      if(this.dataEdit.img.length > 5){
        return true
      } else {
        return false
      }
    }
   },
  },
  methods:{
    resetModal(){
      this.dataEdit = {}
    },
    onClickDataEdit(e){
     e.preventDefault()
      let data = {
        name: this.dataEdit.name,
        sid: this.dataEdit.sid,
        img: this.dataEdit.img,
      }
      // console.log('emit',data)
      this.$emit('emitDataEdit',data)
      this.$nextTick(() => { this.$bvModal.hide("ProfileEdit");});
    }
  },
}
</script>
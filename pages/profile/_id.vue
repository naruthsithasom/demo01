<template>
  <div>
    <b-card
      v-for="item in dataProfile"
      :key="item.id"
      title="Card Title"
      :img-src="`${item.img}`"
      img-alt="Image"
      img-top
      tag="article"
      style="max-width: 20rem"
      class="mb-2"
    >
      <b-card-text>
        sid:
        <h1>{{ item.sid }}</h1>
        name:
        <p>{{ item.name }}</p>
      </b-card-text>

      <b-button href="/" variant="primary">home</b-button>
      <b-button @click="onclickDelete(item.sid)" variant="danger"
        >Delete</b-button
      >
      <b-button @click="onclickEdit(item)" variant="warning">Edit</b-button>
    </b-card>
    <br />
    <button @click="onClickAll">All</button>
    <h1>เพิ่ม Profile</h1>
    e
    <br />
    <div>
      <b-form-input v-model="name" placeholder="Enter your name"></b-form-input>
      <b-form-input v-model="sid" placeholder="Enter your sid"></b-form-input>
      <b-form-input
        v-model="img"
        placeholder="Enter your url image"
      ></b-form-input>
      <button @click="onclickAddimg">Add</button>
    </div>
    <ProfileEdit :dataEdit="dataEdit" @emitDataEdit="onClickNewEdit"/>
  </div>
</template>
<script>
import ProfileEdit from "@/components/ProfileEdit"
export default {
  comments:{
    ProfileEdit
  },
  data() {
    return {
      name: '',
      sid: 0,
      img: '',
      dataTable: [
        {
          sid: 1,
          name: 'john lenon',
          img: 'https://upload.wikimedia.org/wikipedia/commons/8/85/John_Lennon_1969_%28cropped%29.jpg',
        },
        {
          sid: 2,
          name: 'Bob dylan',
          img: 'https://i.guim.co.uk/img/media/789a1844e89b610eeb6289e2d111650f513fbe19/300_1384_3869_2321/master/3869.jpg?width=620&quality=85&auto=format&fit=max&s=e4f7d12ee2a15b3fda518d93a1f87756',
        },
      ],
      dataProfile: [],
      dataEdit:[]
    }
  },
  mounted() {
    this.sid = this.$route.params.id
    let person = this.dataTable.filter((x) => x.sid == this.sid)
    console.log(this.$route.params.id)
    this.dataProfile = [...person]
  },
  methods: {
    onClickAll() {
      return (this.dataProfile = [...this.dataTable])
    },
    onclickAddimg() {
      console.log('name:', this.name + 'sid' + this.sid + 'url:', this.img)
      this.dataTable.push({ sid: this.sid, name: this.name, img: this.img })
      return (this.dataProfile = [...this.dataTable])
    },
    onclickDelete(id) {
      let data = this.dataTable.filter((x) => x.sid != id)
      this.dataProfile = [...data]
      this.dataTable = [...data]
    },
    onclickEdit(data) {
      // let data = this.dataTable.filter((x) => x.sid == id)
      this.dataEdit = {...data}
      this.$bvModal.show("ProfileEdit");
    },
    onClickNewEdit(data){
      console.log('dataedit',data)
    for(let i in this.dataTable){
      if(this.dataTable[i].sid == data.sid){
        this.dataTable[i].name = data.name
        this.dataTable[i].sid = data.sid
        this.dataTable[i].img = data.img
      }
    }
    this.dataProfile = [...this.dataTable]
    }
  },
}
</script>
<style>
</style>
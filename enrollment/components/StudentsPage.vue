<template>
<div>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <nav style="height: 50px">
      <li>
        <div class="icon-bar">
          <b-button v-b-toggle.sidebar-1 vertical class="btn-danger d-block p-3 link-danger text-decoration-none">Menu ☰</b-button>
          <b-sidebar id="sidebar-1" title="Menu" shadow>
            <nav class="mb-3">
            <b-nav vertical>
              <NuxtLink to="/dashboard" class="btn btn-danger navbar-btn fa fa-home"> Home</NuxtLink>
              <NuxtLink to="/addstudents" class="btn btn-danger navbar-btn fa fa-user"> Add Students</NuxtLink>
            </b-nav>
          </nav>
          </b-sidebar>
        </div>
      </li>
      <li style="float:right"><a href="/" class="d-block p-3 link-danger text-decoration-none" title="" data-bs-toggle="tooltip" data-bs-placement="right" data-bs-original-title="Icon-only">
      <svg class="bi" width="40" height="1px"><use xlink:href="#bootstrap"></use></svg>
      <span class="visually-hidden">Logout</span>
    </a></li>
    </nav>
<h1 class="mb-0" style="text-align:center; margin:10px;">Student Enrollment</h1>
<div class="container">
        <br>
          <div class="form-inline" action="#">
              <b-modal id="modal-1" hide-footer title="Add Students">
                <label>ID Number</label><input v-model="item.idnumber" type="number" class="form-control mb-3">
                <label>Last Name</label><input v-model="item.lname" type="text" class="form-control mb-3" >
                <label>First Name</label><input v-model="item.fname" type="text" class="form-control mb-3">
                <label>Phone Number</label><input v-model="item.pnumber" type="number" class="form-control mb-3">
                <label>Date of Birth</label><input v-model="item.dob" type="date" class="form-control mb-3">
                <label>Enrollment Date</label><input v-model="item.ed" type="date" class="form-control mb-3" @keyup.enter="addItem">
                  <div class="modal-footer mt-3">
                    <button class="btn btn-danger" @click="addItem"> Enroll<i class="fa fa-user"></i></button>
                  </div>
              </b-modal>
          </div>
        <br>
      <br>
      <table class="table table-striped table-bordered table-sm">
        <thead class="thead-dark">
          <th style="width:50px">ID</th>
          <th>Last Name</th>
          <th>First Name</th>
          <th>Phone Number</th>
          <th>Date of Birth</th>
          <th>Enrollment Date</th>
          <th class="col-2">Modify</th>
          <th><b-button v-b-modal.modal-1 class="btn-danger fa fa-user">+</b-button></th>
        </thead>
        <tr v-for="item in items" :key="item.idnumber">
          <td>
            <input v-if="item.edit" v-model="item.idnumber" type="number" @keyup.enter="item.edit = !item.edit">
            <span v-else>{{item.idnumber}} </span>
          </td>
          <td>
            <input v-if="item.edit" v-model="item.lname" type="text" @keyup.enter="item.edit = !item.edit">
            <span v-else>{{item.lname}} </span>
          </td>
          <td>
            <input v-if="item.edit" v-model="item.fname" type="text" @keyup.enter="item.edit = !item.edit">
            <span v-else>{{item.fname}} </span>
          </td>
          <td>
            <input v-if="item.edit" v-model="item.pnumber" type="number" @keyup.enter="item.edit = !item.edit">
            <span v-else>{{item.pnumber}} </span>
          </td>
          <td>
            <input v-if="item.edit" v-model="item.sdob" type="date" @keyup.enter="item.edit = !item.edit">
            <span v-else>{{item.dob}} </span>
          </td>
          <td>
            <input v-if="item.edit" v-model="item.ed" type="date" @keyup.enter="item.edit = !item.edit">
            <span v-else>{{item.ed}} </span>
          </td>
          <td><button class="btn btn-success" @click="item.edit = !item.edit">Edit</button>
            <button class="btn btn-secondary" @click="removeItem(item)">Delete</button></td>
        </tr>
      </table>
</div>

  </div>
</template>
<script>

const url = "http://localhost:8081/students";
export default {
    data() {
    return {
      item: {_id: "", idnumber: "",lname: "", fname: "", pnumber: "", dob: "", ed: "", edit: false},
      items: []
    }
  },
  mounted() {
    this.GetAllData()
  },
  methods:{
    async addItem() {
      console.log (this.item.idnumber)
      await this.$axios.$post (url, this.item)
      .then ((res) => {
        console.log(res);
        this.item = {idnumber: "",lname: "", fname: "", pnumber: "", dob: "", ed: "", edit: false};
        this.GetAllData();  
      }
      )
      .catch((err) => console.log(err))
      },
    async removeItem(item){
      await this.$axios.$delete(url + '/' + item._id)
      .then((res) =>{
        console.log(res);
        this.GetAllData();
      })
      .catch((err) => console.log(err))
    },
    GetID(){
      this.item.idnumber = Math.max.apply(Math, this.items.map(function(o){return o.idnumber;}));
      console.log(this.item);
    },
    async GetAllData(){
        await this.$axios.$get(url)
      .then((res) => {
        console.log(res);
        this.tempData = res;
      })
      .catch((err) => console.log(err));
      this.items = this.tempData;
      this.GetCurrentID();
      },
      async ItemEdit(item)
      {
        if(!item.edit)
        {
          item.edit = !item.edit
        }
        else
        {
          item.edit = !item.edit
          console.log(item);
          await this.$axios.$put(url + '/' + item._id, item)
          .then((res) => {
            console.log(res);
          })
          .catch((err) => console.log(err));
        }
      },
      async mounted(){
      await this.GetAllData();
    }
    //  addItem() {
    //    this.items.push({
    //      idnumber:this.item.idnumber ,
    //      lname:this.item.lname, 
    //      fname:this.item.fname, 
    //      pnumber:this.item.pnumber,
    //      dob:this.item.dob, 
    //      ed:this.item.ed,
    //      edit: false}
    //      );
    //    this.item = [];
    //  },
    //  removeItem(index){
    //    this.items.splice(index, 1)
    //  }
  }
}
</script>

<style scoped>
nav {
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
    background-color: #ef3636;
  }

li {
    float: left;
    border-right:1px solid #bbb;
  }

li:last-child {
    border-right: none;
  }

li a {
    display: block;
    color: white;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
  }

li a:hover:not(.active) {
    background-color: #111;
  }

.form-inline input {
  margin-right:8px;
}
</style>

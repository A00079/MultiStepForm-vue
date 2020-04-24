<template>
  <table class="table">
    <thead>
      <tr>
        <th>Name</th>
        <th>Email</th>
        <th>Phone No.</th>
        <th>DOB</th>
        <th>Message</th>
        <th>Website Url</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(item, index) in UserData" :key="index">
        <td>{{item.name}}</td>
        <td>{{item.email}}</td>
        <td>{{item.phoneNo}}</td>
        <td>{{item.dateofbirth}}</td>
        <td>{{item.message}}</td>
        <td>{{item.websiteurl}}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>

export default {
  name: 'Baseformthree',
  data (){
    return {
      UserData:[]
    }
  },
  mounted(){
    var self = this;
    self.$root.$on('FINAL-SAVED-DATA',(data)=>{
      self.UserData.push(data);
    })
  }
}
</script>

<style scoped>
.multi_step_form #msform .action-button {
  background: #5cb85c;
  color: white;
  border: 0 none;
  border-radius: 5px;
  cursor: pointer;
  min-width: 130px;
  font: 700 14px/40px "Roboto", sans-serif;
  border: 1px solid #5cb85c;
  margin: 0 5px;
  text-transform: uppercase;
  display: inline-block;
}
.multi_step_form #msform .action-button:hover, .multi_step_form #msform .action-button:focus {
  background: #405867;
  border-color: #405867;
}
.multi_step_form #msform .previous_button {
  background: transparent;
  color: #99a2a8;
  border-color: #99a2a8;
}
.multi_step_form #msform .previous_button:hover, .multi_step_form #msform .previous_button:focus {
  background: #405867;
  border-color: #405867;
  color: #fff;
}
</style>

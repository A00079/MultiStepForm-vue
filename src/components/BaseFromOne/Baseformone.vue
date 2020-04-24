<template>
  <div class="Form-One">
    <div class="form-row"> 
        <div class="form-group col-md-6" style="margin-left: 25%;">  
            <input  type="text" v-model="formOneData.name" id="name" class="form-control" placeholder="Please enter Name"> 
        </div>  
    </div>   
    <div class="form-row"> 
        <div class="form-group col-md-6" style="margin-left: 25%;"> 
          <input type="text" v-model="formOneData.email" class="form-control" placeholder="Please enter Email" id="email">
        </div>
    </div>
    <div class="form-row"> 
        <div class="form-group  col-md-6" style="margin-left: 25%;"> 
          <input type="number" v-model="formOneData.phoneNo" class="form-control" id="phone" placeholder="Please enter Phone Number">
        </div>
    </div>
      <button type="button" class="next action-button" @click="NextForm">Continue</button>  
  </div>
</template>

<script>

export default {
  name: 'Baseformone',
  data (){
    return {
      formOneData:{
        name:'',
        email:'',
        phoneNo:''
      }
    }
  },
  methods:{
    NextForm(){
      this.validateForm();
      this.$root.$emit('FORM-ONE-DATA',this.formOneData)
      this.$root.$emit('NEXT-FROM',2)
    },
    validateForm(){}
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

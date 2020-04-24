<template>
  <div class="Form-One">
    <div class="form-row"> 
        <div class="form-group col-md-6" style="margin-left: 25%;">  
            <input type="date" v-model="formTowData.dateofbirth" id="dob" class="form-control" placeholder="DOB"> 
        </div>  
    </div>   
    <div class="form-row"> 
        <div class="form-group col-md-6" style="margin-left: 25%;"> 
          <input type="text" v-model="formTowData.message" id="message" class="form-control" placeholder="Message">
        </div>
    </div>
    <div class="form-row"> 
        <div class="form-group  col-md-6" style="margin-left: 25%;"> 
          <input type="text" v-model="formTowData.websiteurl" id="website" class="form-control" placeholder="Website Url">
        </div>
    </div>
      <button type="button" class="action-button previous_button" @click="BackToFormOne">Back</button>
      <button type="button" class="next action-button" @click="SubmitForm">Submit</button>  
  </div>
</template>

<script>

export default {
  name: 'Baseformtwo',
  data (){
    return {
      formOneData:{},
      formTowData:{
        dateofbirth:'',
        message:'',
        websiteurl:''
      }
    }
  },
  mounted(){
    this.$root.$on('FORM-ONE-DATA',(newval)=>{
      this.formOneData = {...newval};
    })
  },
  methods:{
    SubmitForm(){
      let mergeForms = {...this.formOneData,...this.formTowData}
      console.log('mergeForms',mergeForms)
      this.$root.$emit('FINAL-SAVED-DATA',mergeForms)
      this.$root.$emit('NEXT-FROM-SUBMIT',3)
    },
    BackToFormOne(){
      this.$root.$emit('BACK-TO-ONE',1)
    }
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

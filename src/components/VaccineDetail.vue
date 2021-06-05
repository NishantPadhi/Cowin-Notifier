<template>
    <div id="back-img">
        <div>
            <b-form-select v-model="selectedState" :options="states" id="select1" >
            </b-form-select>
            <b-form-select v-model="selectedDistrict" :options="districts"
                            :disabled="selectedState==''" id="select2">
            </b-form-select>
            <b-button size="sm" class="my-2 my-sm-0" type="submit" @click="search()">
            search</b-button>
        </div>

    </div>
</template>
<script>
import moment from 'moment';

export default {
  name: 'VaccineDetail',
  data:function(){
      return{
          states:[{value:'',text:'--select state--'}],
          districts:[{value:'',text:'--select district--'}],
          selectedState:'',
          selectedDistrict:'',
          district_id_selected:-1,
          currentDate:'',
      }
  },
  mounted:function(){
      this.getStates();
      this.currentDate=moment().format('DD-MM-YYYY');
  },
  watch:{
      selectedState:function(state_id){
          this.getDistrict(state_id);
      },
      selectedDistrict:function(district_id){
          this.district_id_selected=district_id;
      }
  },
  methods:{
      getStates:async function(){
          await fetch("https://cdn-api.co-vin.in/api/v2/admin/location/states").then(async response=>{
          let data=await response.text();
          let states=await JSON.parse(data).states;
          console.log(states)
          await states.forEach(x=>{
              this.states.push({value:x.state_id,text:x.state_name})
          });
        });
      },
      getDistrict:function(state_id){
        console.log(`https://cdn-api.co-vin.in/api/v2/admin/location/districts/${state_id}`)
        fetch(`https://cdn-api.co-vin.in/api/v2/admin/location/districts/${state_id}`).then(async response=>{
            let data=await response.text();
            console.log(JSON.parse(data).districts);
            JSON.parse(data).districts.forEach(x=>{
                this.districts.push({value:x.district_id,text:x.district_name})
            });
        })
      },

    search:function(){
        fetch(`https://cdn-api.co-vin.in/api/v2/appointment/sessions/public/findByDistrict?district_id=${this.district_id_selected}&date=${this.currentDate}`).then(async response=>{
            let data=await response.text();
            console.log(JSON.parse(data));
        })
        
    }
  }
}
</script>
<style>
select#select1{
    width:232px !important;
    margin: 350px 5px 350px 500px !important;
}
select#select2{
    width:200px !important;
    margin: 350px 5px 350px 0px !important;
}
.my-sm-0 {
    margin-top: 0 !important;
    margin-bottom: 1px !important;
    height: 25px !important;
}
.btn-sm, .btn-group-sm > .btn {
    padding: 0.08rem 0.5rem 0.5rem 0.5rem !important;
    font-size: 0.875rem !important;
    border-radius: 0.2rem !important;
}
div#back-img{
    background-image:url('./../assets/green4.jpg');
    background-repeat: no-repeat;
    background-size: cover;
}
</style>
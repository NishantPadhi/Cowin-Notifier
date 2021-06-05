<template>
    <div>
        <b-navbar toggleable="lg" type="dark" variant="info" id="bg-color-info">
            <b-navbar-brand href="#">Vaccine Notifier</b-navbar-brand>

            <b-collapse id="nav-collapse" is-nav>
        
                <b-navbar-nav class="ml-auto">

                    <b-nav-form>
                        <b-button size="sm" class="my-2 my-sm-0" 
                                    type="submit" 
                                    v-if="!isUser" id="tooltip-button-1"
                                    v-b-modal.modal-1
                                    @click="signIn()">
                            sign in
                        </b-button>
                        <b-modal 
                            id="modal-1"  
                            :centered=true
                            cancelTitle='NO'>
                            <b-card no-body>
                                <b-tabs card>
                                <b-tab title="Sign In" active>
                                    <b-card-text>
                                    <!--:state="nameState"-->
                                    <b-row class="my-1">
                                      
                                        <b-col sm="12">
                                            <b-form-input id="input-live" 
                                                        v-model="userid" 
                                                        size="sm" 
                                                        placeholder="Enter email id"
                                                        aria-describedby="input-live-help input-live-feedback" 
                                                        trim>
                                            </b-form-input>
                                        </b-col>
                                    </b-row>

                                    <b-row class="my-1">
                                        
                                        <b-col sm="12">
                                            <b-form-input id="input-live" 
                                                            v-model="password" 
                                                            size="sm" 
                                                            type="password"
                                                            placeholder="Enter password"
                                                            aria-describedby="input-live-help input-live-feedback" 
                                                            trim>
                                            </b-form-input>
                                        </b-col>
                                    </b-row>
                                    <b-row class="my-1">
                                        
                                        <b-col sm="12">
                                            <b-button variant="info">Sign In</b-button>
                                        </b-col>
                                    </b-row>
                                        
                                    </b-card-text>
                                </b-tab>
                                <b-tab title="Sign Up">
                                    <b-card-text>
                                    <!--:state="nameState"-->
                                    <b-row class="my-1">
                                      
                                        <b-col sm="12">
                                            <b-form-input id="input-live" 
                                                        v-model="useridSignUp" 
                                                        size="sm" 
                                                        placeholder="Enter email id"
                                                        aria-describedby="input-live-help input-live-feedback" 
                                                        trim>
                                            </b-form-input>
                                        </b-col>
                                    </b-row>

                                    <b-row class="my-1">
                                        
                                        <b-col sm="12">
                                            <b-form-input id="input-live" 
                                                            v-model="passwordSignUp" 
                                                            size="sm" 
                                                            type="password"
                                                            placeholder="Enter password"
                                                            aria-describedby="input-live-help input-live-feedback" 
                                                            trim>
                                            </b-form-input>
                                        </b-col>
                                    </b-row>
                                    <b-row class="my-1">
                                        
                                        <b-col sm="12">
                                            <b-button variant="info">Sign In</b-button>
                                        </b-col>
                                    </b-row>
                                        
                                    </b-card-text>
                                </b-tab>
                                </b-tabs>
                            </b-card>
                        </b-modal>
                        <b-tooltip show placement="lefttop" target="tooltip-button-1">Want to <b>notified</b>?</b-tooltip>
                    </b-nav-form>
                    
                    <b-nav-item-dropdown right v-if="isUser">
                    <template #button-content>
                        <em>User</em>
                    </template>
                    <b-dropdown-item href="#">Profile</b-dropdown-item>
                    <b-dropdown-item href="#">Sign Out</b-dropdown-item>
                    </b-nav-item-dropdown>
                </b-navbar-nav>
            </b-collapse>
        </b-navbar>
    </div>
</template>
<script>
export default {
  name: 'Header',
  data:function(){
      return {
          isUser:false,
          popUpTitle:'Sign In',
          userid:'',
          useridSignUp:'',
          passwordSignUp:'',
        password:'',
      }
  },
  mounted:function(){

  },
  methods:{
    signIn:function(){
        
    }
  }
}
</script>
<style>
.nav-item.b-nav-dropdown.dropdown.show{
    background-color:red;
}
.nav-item.b-nav-dropdown.dropdown{
    text-align:right;
}
.navbar-nav.ml-auto{
    margin-left:93%;
}
.my-2.my-sm-0.padding.btn-secondary.btn-sm.padding-rgt{
    margin-right:5px;
}
.navbar-brand{
    margin-left:10px;
}

#bg-color-info{
    background-color: #008080 !important;
}
#modal-1___BV_modal_content_#modal-1___BV_modal_header_ button, [type=button], [type=reset], [type=submit] {
    -webkit-appearance: media-slider !important;
}
.modal-header {
    padding: 0rem 0rem!important; 
}
.modal-footer {
    visibility: hidden !important;
    display:none !important;
}
.btn-info {
    color: #000;
    background-color: #008080 !important;
    border-color: #008080 !important;
    width:100% !important;
    height:2rem !important;
}
</style>
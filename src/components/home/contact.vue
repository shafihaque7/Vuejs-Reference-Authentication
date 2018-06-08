<template>
   <div class="contact">

      <div v-for="contact in contacts">
         {{ contact.fullName }}
      </div>
   </div>
</template>

<script>
   import axios from 'axios';
   import {AUTH_LOGOUT} from 'actions/auth'
      export default {
        name: 'contact',
        data(){
            return{
               world: "So its working well",
               contacts: []
            }
         },
         mounted () {
            axios
               .get('http://aws.techthatinterest.com/api/contact')
               .then(response => {
                  // console.log(response.data.data)
                  this.contacts = response.data.data;
                  console.log(this.contacts);
               
               })
               .catch(error => {
                  console.log(error)
                  console.log('came here');
                  this.$store.dispatch(AUTH_LOGOUT)
               })
         },
         methods:{
            //   fetchcontact(){

            //   }
         }
      }
</script>
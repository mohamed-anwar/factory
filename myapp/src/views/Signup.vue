<template>
 <v-container>
   <v-layout row>
     <v-flex xs12 sm6 offset-sm3>
       <v-card>
         <v-card-text>
           <v-container>
             <form @submit.prevent="Signup(email,password)">
               <v-layout row>
                 <v-flex xs12 >
                   <v-text-field
                   name="email"
                   label="Mail"
                   id="email"
                   v-model="email"
                   type="email"
                   required>
                   </v-text-field>
                 </v-flex>
               </v-layout>

               <v-layout row>
                 <v-flex xs12 >
                   <v-text-field
                   name="password"
                   label="Password"
                   id="password"
                   v-model="password"
                   type="password"
                   required>
                   </v-text-field>
                 </v-flex>
               </v-layout>


               <v-layout row>
                 <v-flex xs12 >

                  <v-btn type="submit">Sign up</v-btn>
                 </v-flex>
               </v-layout>

             </form>
           </v-container>
        </v-card-text>
       </v-card>
     </v-flex>
   </v-layout>

 </v-container>
</template>


<script>
import firebase from 'firebase';
  export default {
    data () {
      return {
        email:'',
        password:'',

      }
    } ,
    methods:{
       Signup:function(e){
         firebase.auth().createUserWithEmailAndPassword(this.email, this.password).then(
          function(user){
             alert('Account created for ${user.email}');
             this.$router.push('/')
           },
            function(err){
             alert(err.message);
           }
         );
         e.preventDefault();
       }



    }
  }
</script>

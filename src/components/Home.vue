<template>

  <main>
    <br/>
    <v-container fluid ma-0 pa-0 fill-height>
      <v-layout column align-center>
        <v-card  class="mx-auto" color="#26c6da" dark max-width="800">  
          <v-card-title>
            <v-icon large  left > </v-icon>
              <span class="title font-weight-bold">Welcome {{validUserName}}!</span>
          </v-card-title>
         <v-card-text class="headline font-weight-light">
          "Eagle Financial Services, your Midwest Financial Services Partner."
         </v-card-text>
        </v-card >

      </v-layout>
    </v-container>
    <br/> <br/> <br/>

    <v-container fluid fill-height>
      <v-layout justify-center row>
        <v-flex xs12 sm6>
          <v-card>
            <v-container class="blue darken-4" 
              fluid
          
              grid-list-md
            >
              <v-layout row>
                <v-flex xs4>
                  <v-card>
                    <v-img
                      :src="require('@/assets/images/customer.jpg')" height="200px">
                    </v-img>

                    <v-card-actions>
                      <v-btn flat color="blue" @click="viewCustomers">View Details</v-btn>
                    </v-card-actions>
                  </v-card>
                </v-flex>

                <v-flex xs4>
                  <v-card>
                    <v-img
                      :src="require('@/assets/images/nonstock.jpg')" height="200px">
                    </v-img>

                    <v-card-actions>
                      <v-btn flat color="blue" @click="viewInvestments">View Details</v-btn>
                    </v-card-actions>
                  </v-card>
                </v-flex>
                <v-flex xs4>
                  <v-card>
                    <v-img
                      :src="require('@/assets/images/stocks.jpg')" height="200px">
                    </v-img>

                    <v-card-actions>
                      <v-btn flat color="blue" @click="viewStocks">View Details</v-btn>
                    </v-card-actions>
                  </v-card>
                </v-flex>
              </v-layout>
            </v-container>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </main>
  
</template>

<script>
  import router from '../router';

  export default {
    name: 'Home',
    data: () => ({
      validUserName: "Guest"
    }),
    mounted() {
      this.getUser();
    },
    methods: {
      viewCustomers() {
        router.push('/customer-list');
      },
      viewInvestments() {
        router.push('/investment-list');
      },
      viewStocks() {
        router.push('/stock-list');
      },

      
      getUser() {
        if (localStorage.getItem("isAuthenticates")
          && JSON.parse(localStorage.getItem("isAuthenticates")) === true) {
          this.validUserName = JSON.parse(localStorage.getItem("log_user"));
        }
      }



    }
  }
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->

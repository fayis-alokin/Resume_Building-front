<template>

    <div>
        <div class="list-navbar">
            <h2>All Resumes</h2>   
        </div>
        <v-alert v-model="alert"
            dense
            text
            type="success"
            >
            Successfully saved
        </v-alert>

        <div class="list-main">
                <div class="list-search-main">
                    
                    <v-col class="sm-12 md-6 row mt-3 mb-2">
                        <v-text-field placeholder="search by name" solo prepend-inner-icon="mdi-magnify" @keyup.enter="getData()" v-model="query">
                            
                        </v-text-field>
                    </v-col>
                    <div class="list-search-right">
                        <router-link to="/form">+ Add new resume</router-link>
                    </div>
                </div>
                
                <div class="list-table post-table" v-if="data.length == 0 || query===''">
                    <v-simple-table  v-for="item in list" :key="item.basic_details_id">
                       <template v-slot:default>
                        <tr>
                            <th>Name</th>
                            <th>Email</th>
                            <th>Phone</th>
                            <th>Applied Date</th>
                            <th></th>
                        </tr>
                        <tr v-for="i in item" :key="i.basic_details_id" class="data" >
                                <td>{{i.name}}</td>
                                <td>{{i.email}}</td>
                                <td>{{i.phone}}</td>
                                <td>{{i.date_applied}}</td>
                                <td>
                                    <v-menu bottom left>
                                        <template v-slot:activator="{ on, attrs }">
                                    <v-btn
                                      black
                                      icon
                                      v-bind="attrs"
                                      v-on="on"
                                    >
                                      <v-icon>mdi-dots-vertical</v-icon>
                                    </v-btn>
                                  </template>
                      
                                  <v-list>
                                    <v-list-item
                                    >
                                      
                                    <v-list-item-title>
                                        <router-link :to="`/edit/${i.basic_details_id}`" class="edit">Edit</router-link>
                                    </v-list-item-title>
                                      
                                    </v-list-item>
                                    <v-list-item>
                                        <v-list-item-title @click="deleteResume(i.basic_details_id)">Delete</v-list-item-title>
                                    </v-list-item>
                                  </v-list>
                                </v-menu>
                                </td>
                          </tr>
                       </template>
                    </v-simple-table>
                </div>
                <div class="list-table" v-else>
                    <v-simple-table  v-for="item in data" :key="item.basic_details_id">
                        <template v-slot:default>
                          <tr>
                            <th>Name</th>
                            <th>Email</th>
                            <th>Phone</th>
                            <th>Applied on</th>
                            <th></th>
                        </tr>
                              <tr v-for="i in item" :key="i.basic_details_id" class="data" >
                                <td>{{i.name}}</td>
                                <td>{{i.email}}</td>
                                <td>{{i.phone}}</td>
                                <td>{{i.date_applied}}</td>
                                <td>
                                  <v-btn
                          dark
                          icon
                        >
                          <v-icon>mdi-dots-vertical</v-icon>
                        </v-btn>
                                </td>
                            </tr>
                        </template>
                    </v-simple-table>
                </div>
        </div>
        <template>
            <DeleteMessage :dialog="dialog" @delete-id="deleteResume(id)"/>
        </template>
        <!-- <template>
            <ConfirmationMsg :dialog="dialog" @delete-id="deleteResume(id)"/>
          </template>
          <v-list-item class="kebab-menu" @click="getConfirmation(i.basic_details_id)"></v-list-item> -->
    </div>
</template>

<script>

 import axios from 'axios'
 import DeleteMessage from './ConfirmMessage.vue';
 
export default{
    name:'ListingTable',
    components:{
        DeleteMessage
    },
    
    data(){
        return {
            list:[],
            query : "",
            data : [],
            alert:false,
            // dialog:false
        }
    },
    methods :{
        async getData(){
            await axios.get(`http://127.0.0.1:8000/search/${this.query}`)
            .then((response) => {
                this.data = response.data
                console.log(this.data)
            })
            .catch((error) => {
                console.log('error: ',error)
            })
        },
        async deleteResume(id){
            console.log("Deleting resume")
            await axios.delete(`http://127.0.0.1:8000/delete_primary/${id}`)
            .then((res)=> console.log(res.data))
            window.location.reload()
        },
        getConfirmation(id){
        this.dialog=true
        this.delete_id=id
      }
     },
    mounted(){
        axios.get('http://127.0.0.1:8000/get_allprimary')
        .then((resp)=> {
            this.list = resp.data
            console.log(resp.data)
        })

    }
   

}

</script>


<style>

.list-navbar{
    background-color: rgb(26, 90, 90);
    color: whitesmoke;
    padding:20px;
    text-align: left;
}


.list-left{
    background-color: rgb(235, 235, 235);
    width: 15%;
}
.list-heading{
    padding: 10px;
}
.line{
    height: 1px;
    background-color: rgb(151, 146, 146);
    width: 99%;
    margin-left: 10px;
}
.list-search-main{
    display: flex;
    margin: 10px;
    background-color: rgb(255, 255, 255);
}
.list-search-left{
    width: 50%;
    text-align: left;
    padding-left: 5%;
}
.list-search-right{
    width: 50%;
    padding-left: 30%;
    padding-top: 30px;
}
.list-search-right a{
    text-decoration: none;
    font-size: 15px;
}
.list-search-left input{
    width: 60%;
    height: 4vh;
    padding: 15px;
    border: 1px solid;
   
}
.list-search-left input:focus{
    outline: none;
}

.table-heading{
    
    color: aliceblue;
   
}
.v-text-field__details{
    display: none;
}
th{
    width: 400px;
    text-align: center;
    vertical-align: middle;
    padding: 10px 0;
    background-color: teal;
    color: rgb(255, 255, 255);
}

.data td{
    text-align: center;
}

.data:hover{
  background-color: rgb(236, 230, 222);
}

.v-list-item:hover{
    background-color: rgb(218, 218, 218);
    cursor: pointer;
}
.edit{
    text-decoration: none;
}




</style>














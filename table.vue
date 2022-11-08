<template>
    <div class="menu-bar">
        <h4>Resume Building Application</h4>
    </div>
    <div class="main-container">
        <div class="main-heading">
            <h2>Resumes</h2>
        </div>
        <div class="line">
        </div>
        <div class="search-area">
            <div class="search-bar">
                <input type="text" placeholder="Search by name or email">
            </div>
            <div class="add-new-resume">
                <a href="">+ Add new resume</a>
            </div>
        </div>
        <div class="list-table">
            <table>
                <tr>
                    <th>Name</th>
                    <th>Email</th>
                    <th>Phone</th>
                    <th>Applied on</th>
                </tr>
               <tr v-for="post in posts" :key="post.basic_details_id">
                    <div v-for="i in post" :key="i.basic_details_id" class="data" >
                        <td>{{i.name}}</td>
                        <td>{{i.email}}</td>
                        <td>{{i.phone}}</td>
                        <td>{{i.applied_date}}</td>
                    </div>

               </tr>
            </table>
        </div>
    </div>   
</template>

<script>

import axios from 'axios'

export default{
    name:"listing_table",
    data() {
        return {
            posts: []
        }
    },
    mounted(){
    
        axios.get('http://127.0.0.1:8000/all-resume')
        .then((res)=>{
            this.posts = res.data
            console.log('data:',res.data)
        })
        // .catch(function(error){
        //     console.log('error:',error)
        // })
    
    }
   

}
</script>

<style>
.menu-bar{
    background-color: black;
    color: white;
    height: 7vh;
    padding: 10px;
}
.main-heading{
    margin-left: 30px;
}
.main-heading{
    padding: 10px;
}
.line{
    height: 1px;
    background-color: black;
    width: 99%;
    margin-left: 10px;
}
.search-area{
    display: flex;
    margin: 20px;
}
.search-bar{
    width: 80%;
}
.add-new-resume{
    width: 20%;

}
.add-new-resume a{
    text-decoration: none;
}
input{
    width: 50%;
    height: 5vh;
    border-radius: 5px;
}
th,td{
    width:10%
}
</style>
<template>
    <div class="container">
      <div class="row">
        <div class="col-12 text-center">
          <h4 class="pt-3">Add new Category</h4>
        </div>
      </div>
 
      <div class="row">
        <div class="col-3"></div>
        <div class="col-md-6 px-5 px-md-0">
         <form>
           <div class="form-group">
             <label>Category Name</label>
             <input type="text" class="form-control" v-model="categoryName" required>
           </div>
           <div class="form-group">
             <label>Description</label>
             <input type="text" class="form-control" v-model="description" required>
           </div>
           <div class="form-group">
             <label>ImageURL</label>
             <input type="url" class="form-control" v-model="imageURL" required>
           </div>
           <button type="button" class="btn btn-primary" @click="addCategory">Submit</button>
         </form>
        </div>
        <div class="col-3"></div>
      </div>
   </div>
 </template>
 
 <script>
import axios from 'axios';

 export default {
   data(){
     return {
       categoryName : null,
       description : null,
       imageURL : null,
     }
   },
   methods : {
     async addCategory() {
       const newCategory = {
         categoryName : this.categoryName,
         description : this.description,
         imageUrl : this.imageURL,
       };
       
       const baseURL = "http://localhost:8000/";

       await axios({
         method: 'post',
         url: baseURL+"category/",
         data : JSON.stringify(newCategory),
         headers: {
           'Content-Type': 'application/json'
         }
       })
       .then(() => {
        console.log("Category Added Successfully")
       })
       .catch(err => console.log(err));
     }
   },
   mounted(){
   }
 }
 </script>
 
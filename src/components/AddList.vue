<template>
    <div >
        <!-- <FormAdd v-on:submit-item="submit" /> -->
        
        <FormAdd v-bind:edit-index="editIndex" v-bind:name="name" v-on:edit-item="edit" v-on:submit-item="submit" />


        <ul >
            <li v-for="(item, index) in items" v-bind:key="index">
                <span >{{ item }}</span>
                <div >

                    <i class="fa-solid fa-trash" v-on:click.prevent="deleteItem(index)"></i>
                </div>
                <div >
                    <i class="fa-regular fa-pen-to-square" v-on:click.prevent="editItem(index)"></i>
                 
                </div>
                
            </li>
        </ul>
    </div>
</template>

<script>

import FormAdd from './FormAdd.vue'

export default {
    name: `AddList`,
    components: {
        FormAdd
    },

    data() {
        return {

            items:[],
            name:"",
            editIndex: -1
        }
    },
    methods: {
        submit: function(name) {
            this.items.push(name);
            this.name = "";
        },
       
        
        edit: function(obj){

         var {name, editIndex} =obj;
         console.log("actual edit",name, editIndex);
         this.items.splice(editIndex,1, name);
          this.name= "";
           this.editIndex = -1;
          },


        deleteItem: function (index) {
            this.items.splice(index,1);
        },
        
        // deleteItem: function(index){
        //     this.data.splice(index, 1);
        // ,
        editItem: function(index){
            console.log("edit index");
            this.editIndex = index;
            this.name = this.items[index];
        
         }
    }
};






</script>


<style scoped>

  
</style>
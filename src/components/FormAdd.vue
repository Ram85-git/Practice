<template>
    <div>Form
        <p>Enter something</p>
        <i>Press enter</i>
        <br/>
        <form v-on:submit.prevent>
            <input v-on:keypress="submit" type="text" v-model="text"/>
        </form>
    </div>

</template>

<script>

export default{
    name:`AddForm`,
    data(){
        return {
            text:"",



            // editIndex:false
        }
    },

    watch: {
        name: function(newName){
            console.log("watch  ", newName);
            this.text = newName;
        }

    },
    props: {
        name: {
            type: String,
            requried: true
        },
        editIndex: {
            type: Number,
            requried: true
        }
    },

    methods: {
        submit:function(e){

            if(e.keyCode===13){
                // this.$emit("submit-item",this.name);
                // this.name="";

             if(this.editIndex !==-1){

                console.log("edit-item");
                this.$emit("edit-item",{
                    name:this.text,
                    editIndex: this.editIndex
                });
             } else {
                this.$emit("submit-item",this.text);
             }

             this.text ="";



            }

        }
    }

}


</script>
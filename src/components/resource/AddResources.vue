<template>
    <h2>Add resources</h2>
     <base-dialog v-if='invalidInput' title='Invalid input' @close='confirmError'>
        <template #default>
            <p> At least one input value is invalid</p>
            <p> Please Check all your inputs</p>
        </template>
        <template #actions>
            <base-button @click='confirmError'>Okay</base-button>
        </template>
    
    </base-dialog>
    <form @submit.prevent='addResource'>
        <div class="form-control">
            <label for='title'></label>
            <input type='text' name='title' id='title' ref='titleInput'>
        </div>
        <div class="form-control">
            <label for='desc'>Description</label>
            <textarea name='desc' id='desc' rows='3' ref='descInput'></textarea>
        </div>
        <div class="form-control">
            <label for='link'>Link</label>
            <input type='url' name='link' id='link' ref='linkInput'>
        </div>
        <base-button >Add resource</base-button>
    </form>
   
</template>

<script>
import BaseDialog from '../layouts/BaseDialog.vue';

export default {
  components: { BaseDialog },
  

    inject:['submitData'],

    data(){
        return {
            invalidInput: false,
        }
    },

    methods:{
        addResource(){
            const enteredName = this.$refs.titleInput.value;
            const enteredDesc = this.$refs.descInput.value;
            const enteredlink = this.$refs.linkInput.value;

            if(enteredName.trim() === '' || enteredlink.trim() === '' || enteredDesc.trim() === '')
            {
               this.confirmError();
               return
            }

        this.submitData(enteredName,enteredDesc,enteredlink)
        },
        confirmError(){
            this.invalidInput = !this.invalidInput;
        }
    }
}
</script>
<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>


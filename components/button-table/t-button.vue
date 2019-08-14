<template>
  <div>
    <b-button v-b-modal.modal-prevent-closing>Open Modal</b-button>

    <div class="mt-3">
      Submitted Names:
      <div v-if="submittedNames.length === 0">--</div>
      <ul v-else class="mb-0 pl-3">
        <li v-for="name in submittedNames" :key="name">
          
        </li>
      </ul>

    </div>

    <b-modal
      id="modal-prevent-closing"
      ref="modal"
      title="Submit Your Name"
      @show="resetModal"
      @hidden="resetModal"
      @ok="handleOk"
    >
      <form ref="form" @submit.stop.prevent="handleSubmit">
        <b-form-group
          :state="nameState"
          label="Name"
          label-for="name-input"
          invalid-feedback="Name is required"
        >
          <b-form-input
            id="name-input"
            v-model="form.name"
            :state="nameState"
            required
          ></b-form-input>
        </b-form-group>

        <b-form-group
          :state="nameState"
          label="First name"
          label-for="name-input"
          invalid-feedback="Name is required"
        >
          <b-form-input
            id="name-input"
            v-model="form.firstname"
            :state="nameState"
            required
          ></b-form-input>
        </b-form-group>

        <b-form-group
          :state="nameState"
          label="Last Name"
          label-for="name-input"
          invalid-feedback="Name is required"
        >
          <b-form-input
            id="name-input"
            v-model="form.lastname"
            :state="nameState"
            required
          ></b-form-input>
        </b-form-group>

        <b-form-group
          :state="nameState"
          label="Age"
          label-for="name-input"
          invalid-feedback="Name is required"
        >
          <b-form-input
            id="name-input"
            v-model="form.age"
            :state="nameState"
            required
          ></b-form-input>
        </b-form-group>
      </form>
    </b-modal>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        name: '',
        nameState: null,
        submittedNames: [],
        form: {
          firstname:'',
          lastname:'',
          age:''
        }
      }
    },
    computed:{
      getFullName(){
        app: return this.firstname +" "+ this.lastname;
      }
    },
    methods: {

      checkFormValidity() {
        const valid = this.$refs.form.checkValidity()
        this.nameState = valid ? 'valid' : 'invalid'
        return valid
      },
      resetModal() {
        this.name = ''
        this.firstname = ''
        this.lastname = ''
        this.age = ''
        this.nameState = null
      },
      handleOk(bvModalEvt) {  // Prevent modal from closing
        
        bvModalEvt.preventDefault()  // Trigger submit handler
        
        this.handleSubmit()
      },
      handleSubmit() {
        
        if (!this.checkFormValidity()) {  // Exit when the form isn't valid
          return
        }
        
        //this.submittedNames.push(this.name, this.getFullName, this.age) // Push the name to submitted names
       
        this.$nextTick(() => {  // Hide the modal manually
          this.$refs.modal.hide()
        })

        let input = { 
          isActive: true, 
          age: this.form.age, 
          first_name: this.form.firstname, 
          last_name: this.form.lastname 
        }
        this.$emit('addData', input)
      }
    }
  }
</script>
<template>
  <div id="app">
    <div class="container mt-5">
      <div class="row">
        <div class="col-sm-6 mx-auto">
          <form @submit.prevent="regUser" novalidate>
            
            <div v-show = "step === 1" class="step">

              <div class="progress">
                <div class="progress-bar" role="progressbar" style="width: 25%;" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100">25%</div>
              </div>

              <div class="form-group mt-5">
                <label for="name">Name</label>
                <input v-model="formReg.name" type="text" class="form-control" id="name">
              </div>
              
              <div class="form-group">
                <label for="surname">Surname</label>
                <input v-model="formReg.surname" type="text" class="form-control" id="surname">
              </div>

              <div class="form-group">
                <label for="email">Email</label>
                <input v-model="formReg.email" type="text" class="form-control" id="email">
              </div>

              <button @click= "nextStep" type="button" class="btn btn-primary">Next</button>

            </div>

            <transition name="slide-fade">
              <div v-show = "step === 2" class="step">
                <div class="progress">
                  <div class="progress-bar" role="progressbar" style="width: 75%;" aria-valuenow="75" aria-valuemin="0" aria-valuemax="100">75%</div>
                </div>

                <div class="form-group mt-5">
                  <label for="phone">Phone</label>
                  <input v-model="formReg.phone" type="tel" class="form-control" id="phone">
                </div>
                
                <div class="form-group">
                  <label for="country">Country</label>
                  <input v-model="formReg.country" type="text" class="form-control" id="country">
                </div>

                <div class="form-group">
                  <label for="city">City</label>
                  <input v-model="formReg.city" type="text" class="form-control" id="city">
                </div>

                <button @click= "backStep" type="button" class="btn btn-primary mr-2">Back</button>
                <button @click= "nextStep" type="button" class="btn btn-primary">Next</button>
              </div>
            </transition>

            <transition name="slide-fade">
              <div v-show = "step === 3" class="step">
                <div class="progress">
                  <div class="progress-bar" role="progressbar" style="width: 100%;" aria-valuenow="100" aria-valuemin="0" aria-valuemax="100">100%</div>
                </div>

                <div class="form-group mt-5">
                  <label for="password">Password</label>
                  <input v-model="formReg.password" type="password" class="form-control" id="password">
                </div>
                
                <div class="form-group">
                  <label for="passwordConfirm">Password Confirm</label>
                  <input v-model="formReg.passwordConfirm" type="password" class="form-control" id="passwordConfirm">
                </div>

                <button @click= "backStep" type="button" class="btn btn-primary mr-2">Back</button>
                <button type="submit" class="btn btn-primary">Registration</button>
              </div>
            </transition>

          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      step: 1,
      show: true,
      formReg:{
        name:'',
        surname:'',
        email:'',
        phone:'',
        country:'',
        city:'',
        password:'',
        passwordConfirm:''
      }
    }
  },
  methods: {
    nextStep() {
      if(this.step < 3){
        this.step++
      }
      
    },
    backStep() {
      if(this.step > 1){
        this.step--
      }
    },
    regUser(){
      console.log('Reg Done!')
    }
  }
}
</script>

<style>
.slide-fade-enter-active {
  transition: all 0.3s ease;
}

.slide-fade-enter {
  transform: translateX(10px);
  opacity: 0;
}
</style>

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
                <input @blur= "$v.formReg.name.$touch()" 
                        :class="{ 'is-invalid': $v.formReg.name.$error}"
                        v-model="formReg.name" 
                        type="text" class="form-control" id="name">
                <div v-if= "!$v.formReg.name.required" class="invalid-feedback">
                  Please enter your Name.
                </div>
                <div v-if= "!$v.formReg.name.alpha" class="invalid-feedback">
                  Please enter only text.
                </div>
              </div>
              
              <div class="form-group">
                <label for="surname">Surname</label>
                <input @blur= "$v.formReg.surname.$touch()" 
                        :class="{ 'is-invalid': $v.formReg.surname.$error}"
                        v-model="formReg.surname" 
                        type="text" class="form-control" id="surname">
                <div v-if= "!$v.formReg.surname.required" class="invalid-feedback">
                  Please enter your Surname.
                </div>
                <div v-if= "!$v.formReg.surname.alpha" class="invalid-feedback">
                  Please enter only text.
                </div>
              </div>

              <div class="form-group">
                <label for="email">Email</label>
                <input @blur= "$v.formReg.email.$touch()" 
                        v-model="formReg.email" 
                        :class="{ 'is-invalid': $v.formReg.email.$error}"
                        type="text" class="form-control" id="email">
                <div v-if= "!$v.formReg.email.required" class="invalid-feedback">
                  Please enter your email.
                </div>

                <div v-if= "!$v.formReg.email.email" class="invalid-feedback">
                  Please enter correct your email.
                </div>

              </div>

              <button @click= "nextStep" 
                      :disabled= "$v.formReg.name.$invalid || $v.formReg.surname.$invalid || $v.formReg.email.$invalid"
                      type="button" class="btn btn-primary">Next</button>
            </div>

            <transition name="slide-fade">
              <div v-show = "step === 2" class="step">
                <div class="progress">
                  <div class="progress-bar" role="progressbar" style="width: 75%;" aria-valuenow="75" aria-valuemin="0" aria-valuemax="100">75%</div>
                </div>

                <div class="form-group mt-5">
                  <label for="phone">Phone</label>
                  <input @blur= "$v.formReg.phone.$touch()" 
                          :class="{ 'is-invalid': $v.formReg.phone.$error}"
                          v-model="formReg.phone" 
                          type="tel" class="form-control" id="phone">
                  <div v-if= "!$v.formReg.phone.required" class="invalid-feedback">
                    Please enter your phone.
                  </div>
                </div>
                
                <div class="form-group">
                  <label for="country">Country</label>
                  <input @blur= "$v.formReg.country.$touch()" 
                          :class="{ 'is-invalid': $v.formReg.country.$error}"
                          v-model="formReg.country" 
                          type="text" class="form-control" id="country">
                  <div v-if= "!$v.formReg.country.required" class="invalid-feedback">
                    Please enter your country.
                  </div>
                  <div v-if= "!$v.formReg.country.alpha" class="invalid-feedback">
                    Please enter only text.
                  </div>
                </div>

                <div class="form-group">
                  <label for="city">City</label>
                  <input @blur= "$v.formReg.city.$touch()" 
                          :class="{ 'is-invalid': $v.formReg.city.$error}"
                          v-model="formReg.city" 
                          type="text" class="form-control" id="city">
                  <div v-if= "!$v.formReg.city.required" class="invalid-feedback">
                    Please enter your city.
                  </div>
                  <div v-if= "!$v.formReg.city.alpha" class="invalid-feedback">
                    Please enter only text.
                  </div>
                </div>

                <button @click= "backStep" type="button" class="btn btn-primary mr-2">Back</button>
                <button @click= "nextStep" 
                        :disabled= "$v.formReg.phone.$invalid || $v.formReg.country.$invalid || $v.formReg.city.$invalid"
                        type="button" class="btn btn-primary">Next</button>
              </div>
            </transition>

            <transition name="slide-fade">
              <div v-show = "step === 3" class="step">
                <div class="progress">
                  <div class="progress-bar" role="progressbar" style="width: 100%;" aria-valuenow="100" aria-valuemin="0" aria-valuemax="100">100%</div>
                </div>

                <div class="form-group mt-5">
                  <label for="password">Password</label>
                  <input @blur= "$v.formReg.password.$touch()" 
                          :class="{ 'is-invalid': $v.formReg.password.$error}"
                          v-model="formReg.password" type="password" class="form-control" id="password">
                  <div v-if= "!$v.formReg.password.required" class="invalid-feedback">
                    Please create password.
                  </div>
                  <div v-if= "!$v.formReg.password.minLength" class="invalid-feedback">
                    Please enter minimum 6.
                </div>
                </div>
                
                <div class="form-group">
                  <label for="passwordConfirm">Password Confirm</label>
                  <input @blur= "$v.formReg.passwordConfirm.$touch()" 
                          :class="{ 'is-invalid': $v.formReg.passwordConfirm.$error}"
                          v-model="formReg.passwordConfirm" 
                          type="password" class="form-control" id="passwordConfirm">
                  <div v-if= "!$v.formReg.passwordConfirm.sameAs" class="invalid-feedback">
                    Please confirm password.
                  </div>
                </div>

                <button @click= "backStep" type="button" class="btn btn-primary mr-2">Back</button>
                <button type="submit" 
                        :disabled= "$v.formReg.password.$invalid || $v.formReg.passwordConfirm.$invalid"
                        class="btn btn-primary">Registration</button>
              </div>
            </transition>

          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { required, minLength, email, sameAs, helpers } from 'vuelidate/lib/validators'
const alpha = helpers.regex('alpha', /^[a-zA-Zа-яёА-ЯЁ]*$/)

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
  },
  validations: {
    formReg: {
        name: {
          required,
          alpha,
        },
        surname: {
          required,
          alpha,          
        },
        email: {
          required,
          email
        },
        phone: {
          required
        },
        country: {
          required,
          alpha
        },
        city: {
          required,
          alpha
        },
        password: {
          required,
          minLength: minLength(6)
        },
        passwordConfirm: {
          sameAs: sameAs('password')
        }
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

<template>
  <div id="app">
    <div class="container mt-5">
      <div class="row">
        <div class="col-sm-6 mx-auto">
          <form>
            
            <div v-show = "step === 1" class="step">

              <div class="form-group">
                <label for="name">Name</label>
                <input type="text" class="form-control" id="name">
              </div>
              
              <div class="form-group">
                <label for="surname">Surname</label>
                <input type="text" class="form-control" id="surname">
              </div>

              <div class="form-group">
                <label for="email">Email</label>
                <input type="text" class="form-control" id="email">
              </div>

              <button @click= "nextStep" type="button" class="btn btn-primary">Next</button>

            </div>

            <div v-show = "step === 2" class="step">

              <div class="form-group">
                <label for="password">Password</label>
                <input type="password" class="form-control" id="password">
              </div>
              
              <div class="form-group">
                <label for="passwordConfirm">Password Confirm</label>
                <input type="password" class="form-control" id="passwordConfirm">
              </div>

              <button @click= "backStep" type="button" class="btn btn-primary mr-2">Back</button>
              <button @click= "nextStep" type="button" class="btn btn-primary">Next</button>

            </div>

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
      step: 1
    }
  },
  methods: {
    nextStep() {
      this.step++
    },
    backStep() {
      this.step--
    }
  }
}
</script>

<style>

</style>

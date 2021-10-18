<template>
  <div class="row min-height">
    <div
      class="
        left
        col-4
        min-height
        orange-backdrop
        d-grid
        place-content-end
        p-b-50
      "
    >
      <span>
        <img src="~/assets/images/image1.png" alt="" />
      </span>
    </div>
    <div class="right col-8 full-height">
      <div class="container">
        <div class="d-flex justify-end">
          <button class="button button-fill-red">
            <p class="p-r-5 p-l-5 p-t-2 p-b-2">Logout</p>
          </button>
        </div>

        <!-- step navigation -->
        <step-navigation
          class="m-t-20"
          :disabled="[verify, social, business]"
          :step-count="stepCounter"
          @stepper="move($event)"
        />

        <hr class="m-t-15" />
        <div class="content">
          <!-- step {{ stepCounter }} / 3 -->
          <div>
            <template v-if="stepCounter === 0">
              <Verify />
            </template>
            <template v-if="stepCounter === 1">
              <Social />
            </template>
            <template v-if="stepCounter === 2">
              <BusinessCategory />
            </template>
          </div>
         <div class=" d-flex justify-end m-t-8">
            <button class="button button-fill-blue" @click="increaseStep">
            <p class="p-r-5 p-l-5 p-t-2 p-b-2" v-if="stepCounter === 0">
              Continue
            </p>
            <p class="p-r-5 p-l-5 p-t-2 p-b-2" v-else-if="stepCounter === 1">
              Confirm Social Handles
            </p>
            <p class="p-r-5 p-l-5 p-t-2 p-b-2" v-else>Complete</p>
          </button>
         </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      verify: { id: 0, isDisabled: false },
      social: { id: 1, isDisabled: false },
      business: { id: 2, isDisabled: false },
      stepCounter: 0,
    };
  },
  methods: {
    move(e) {
       this.stepCounter = e
      console.log(e);
    },
    increaseStep(){
      this.stepCounter++
    }
  },
};
</script>
<style scoped>
/* Extra small devices (phones, 600px and down) */
@media only screen and (max-width: 42em) {
  .left {
    display: none;
  }
}
</style>
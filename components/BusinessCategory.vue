<template>
  <div>
    <div class="m-b-25 m-t-25">
      <h2 class="f-size-7">Business Category</h2>
    </div>
    <div class="d-flex items-center col-12 m-t-10 m-b-14 desktop-input">
      <div class="col-6 m-r-8">
        <label for="abeg_tag" class="m-b-3 text-medium f-size-3"
          >Type of your business</label
        >
        <base-select
          :options="['lorem', 'ipsum', 'esut', 'sitem']"
          :default="'lorem'"
          class="select m-t-6"
          @input="displayToKey($event)"
        />
      </div>
      <div class="col-6 m-l-8">
        <label for="abeg_tag" class="m-b-3 text-medium f-size-3"
          >Business Category</label
        >
        <base-select
          :options="['lorem', 'ipsum', 'esut', 'sitem']"
          :default="'lorem'"
          class="select m-t-6"
          @input="displayToKey($event)"
        />
      </div>
    </div>
    <div>
      <p class="f-size-3 text-medium m-b-4">
        Do you use POS machines for your business?
      </p>
      <div class="d-flex items-center">
        <button
          class="button button-outline-gray m-r-9"
          @click="changeTab('bvn')"
        >
          <p class="p-r-2 p-l-2 p-t-1 p-b-1 f-size-4">Yes</p>
        </button>
        <button
          class="button button-outline"
          @click="changeTab('account_number')"
        >
          <p class="p-r-2 p-l-2 p-t-1 p-b-1 f-size-4">No</p>
        </button>
      </div>
    </div>
    <hr class="m-t-20" />
  </div>
</template>


<script>
import BaseSelect from './BaseSelect.vue';
export default {
  components: { BaseSelect },
  name: "BusinessCategory",
  methods:{
    displayToKey(e){
      console.log(e)
    }
  }
};
</script>

<style lang="scss" scoped>
@media ( max-width: 42.85em) {
  .desktop-input {
    flex-direction: column;
  }
  .m-l-8{
    margin-left: 0;
  }
  .m-r-8{
    margin-right: 0;
  }
}
</style>
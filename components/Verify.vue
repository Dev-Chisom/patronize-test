<template>
  <div>
    <h2 class="m-b-25 m-t-25 f-size-7">Verify Account</h2>
    <p class="f-size-3 text-medium m-b-4">Select a verification method</p>
    <div class="d-flex items-center">
      <button
        class="button button-outline m-r-9"
        :class="[tab === 'bvn' ? 'button-outline' : 'button-outline-gray']"
        @click="changeTab('bvn')"
      >
        <p class="p-r-2 p-l-2 p-t-1 p-b-1 f-size-4">BVN</p>
      </button>
      <button
        class="button"
        :class="[
          tab === 'account_number' ? 'button-outline' : 'button-outline-gray',
        ]"
        @click="changeTab('account_number')"
      >
        <p class="p-r-2 p-l-2 p-t-1 p-b-1 f-size-4">Personal Account Number</p>
      </button>
    </div>
    <div class="m-t-20">
      <div v-if="tab == 'bvn'">
        <label for="bvn" class="f-size-3 text-medium m-b-4">
          Bank Verification Number (11-digits)
        </label>
        <input type="number" id="bvn" maxlength="11" />

        <div>
          <accordion>
            <accordion-item> </accordion-item>
          </accordion>
        </div>
      </div>
      <div v-if="tab == 'account_number'">
        <div class="d-flex items-center desktop-input">
          <div class="m-r-18 col-s-12">
            <label for="account_number" class="f-size-3 text-medium m-b-4"
              >Account Number</label
            >
            <input type="number" id="account_number" />
          </div>
          <div class="m-l-18 col-s-12">
            <label for="account_number" class="f-size-3 text-medium m-b-4"
              >Select Bank</label
            >
            <base-select
              :options="['lorem', 'ipsum', 'esut', 'sitem']"
              :default="'lorem'"
              class="select mb-6"
              @input="displayToKey($event)"
            />
          </div>
        </div>
      </div>

      <hr class="m-t-20" />
    </div>
  </div>
</template>

<script>
import BaseSelect from "./BaseSelect.vue";
export default {
  name: "Verify",
  components: { BaseSelect },
  data() {
    return {
      tab: "bvn",
    };
  },
  methods: {
    changeTab(tab) {
      this.tab = tab;
    },
    displayToKey(e){
      console.log(e)
    }
  },
};
</script>

<style lang="scss">
@media ( max-width: 42.85em) {
  .desktop-input {
    flex-direction: column;
  }
  .m-l-18{
    margin-left: 0;
  }
  .m-r-18{
    margin-right: 0;
  }
}
</style>
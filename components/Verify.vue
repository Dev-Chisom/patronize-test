<template>
  <div>
    <h2 class="m-b-25 m-t-25 f-size-7">Verify Account</h2>
    <p class="f-size-3 text-medium m-b-4">Select a verification method</p>
    <div class="d-flex items-center">
      <button
        class="button button-outline m-r-8"
        :class="
         [ tab === 'bvn' ? 'button-outline' : 'button-outline-gray']
        "
        @click="changeTab('bvn')"
      >
        <p class="p-r-2 p-l-2 p-t-1 p-b-1 f-size-4">BVN</p>
      </button>
      <button
        class="button "
         :class="
          [tab === 'account_number' ? 'button-outline' : 'button-outline-gray']
        "
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
        <div class="d-flex items-center">
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
            <select name="bank" id="" class="m-t-4">
                <option value="1">FCMB</option>
            </select>
          </div>
        </div>
        <hr  class="m-t-18"/>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Verify",
  data() {
    return {
      tab: "bvn",
    };
  },
  methods: {
    changeTab(tab) {
      this.tab = tab;
    },
  },
};
</script>

<style lang="scss" scoped>
select{
    // -webkit-appearance: none;
    // -moz-appearance: none;
    // background: transparent;
    // background-image: url("~/assets/images/icons/caret-down.svg");
    // background-repeat: no-repeat;
    // background-position-x: 100%;
    // background-position-y: 5px;
    border: 1px solid #E4E9EF;
    border-radius: 10px;
    margin-right: 2rem;
    height: 54px;
    padding: 1rem;
    padding-right: 2rem;
    width: 100%;
    outline: none;
}
</style>
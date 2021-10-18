<template>
  <li class="accordion__item m-b-5 m-t-9 ">
    <div
      class="accordion__trigger"
      :class="{ accordion__trigger_active: visible }"
      @click="open"
    >
      <!-- This slot will handle the title/header of the accordion and is the part you click on -->
      <slot name="accordion-trigger">
        <div class="d-flex m-l-4">
          <img
            src="~/assets/images/icons/union.svg"
            alt="union"
            class="h-2 w-3"
          />
          <small class="f-size-3 text-medium m-l-3">Why we need your BVN</small>
        </div>
        <div class="d-flex m-r-4">
          <small class="primary-blue">{{ visible ? "Hide" : "Show" }}</small>
          <img
            src="~/assets/images/icons/chevron-down.svg"
            alt="chevron up"
            class="h-2 w-2"
            v-if="visible"
          />
          <img
            src="~/assets/images/icons/chevron-up.svg"
            alt="chevron up"
            class="h-2 w-2"
            v-else
          />
        </div>
      </slot>
    </div>

    <transition
      name="accordion"
      @enter="start"
      @after-enter="end"
      @before-leave="start"
      @after-leave="end"
    >
      <div class="accordion__content m-l-18 m-r-18 m-b-4" v-show="visible">
        <p class="f-size-3 text-regular">We only need access to your:</p>
        <ul class="m-b-4">
          <li class="d-flex f-size-3 text-regular m-a-3"> <img
            src="~/assets/images/icons/green-tick.svg"
            alt="chevron up"
            class="h-2 w-2 m-r-2"
          />Full Name</li>
          <li class="d-flex f-size-3 text-regular m-a-3"><img
            src="~/assets/images/icons/green-tick.svg"
            alt="chevron up"
            class="h-2 w-2 m-r-2"
          />Phone Number</li>
          <li class="d-flex f-size-3 text-regular m-a-3"><img
            src="~/assets/images/icons/green-tick.svg"
            alt="chevron up"
            class="h-2 w-2 m-r-2"
          />Date of Birth</li>
        </ul>
        
        <hr class="m-t-15"/>
        <div>
          <img
            src="~/assets/images/icons/key.svg"
            alt="chevron up"
            class="h-2 w-2 m-r-2"
          />
          <p class="f-size-3 text-regular m-b-10">🔐 Your BVN does not give us access to your bank accounts or transactions</p>
        </div>
      </div>
    </transition>
  </li>
</template>


<script>
export default {
  props: {},
  inject: ["Accordion"],
  data() {
    return {
      index: null,
    };
  },
  computed: {
    visible() {
      return this.index == this.Accordion.active;
    },
  },
  methods: {
    open() {
      if (this.visible) {
        this.Accordion.active = null;
      } else {
        this.Accordion.active = this.index;
      }
    },
    start(el) {
      el.style.height = el.scrollHeight + "px";
    },
    end(el) {
      el.style.height = "";
    },
  },
  created() {
    this.index = this.Accordion.count++;
  },
};
</script>

<style lang="scss" scoped>
.accordion__item {
  cursor: pointer;
  border-bottom: 1px solid #ebebeb;
  position: relative;
  background-color: #e9eef4;
  border-radius: 10px;
}

.accordion__trigger {
  display: flex;
  justify-content: space-between;
  padding: 27px 0;
  // height: 62px;
}

.accordion-enter-active,
.accordion-leave-active {
  will-change: height, opacity;
  transition: height 0.3s ease, opacity 0.3s ease;
  overflow: hidden;
}

.accordion-enter,
.accordion-leave-to {
  height: 0 !important;
  opacity: 0;
}
.accordion__content {
  background-color: #e9eef4;
  border-radius: 10px;
  height: 196px;
}
.accordion__content > hr{
  border: 1px solid #a5b4cb;
  width: 100%;
}
</style>

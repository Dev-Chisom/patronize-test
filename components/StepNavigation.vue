<template>
  <div class="d-flex">
    <button
      v-for="(step, index) in steps"
      :key="index"
      type="button"
      class="d-flex items-center m-r-20"
      @click.prevent="moveToStep(index)"
    >
      <button
        class="button grey-bg mobile"
        style="border-radius: 3.1px; padding: 16px 16px;"
        v-if="stepCount > index"
      >
        <svg
          class="w-2 h-2"
          width="13"
          height="9"
          viewBox="0 0 13 9"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M1.99854 4.49751L5.00103 7.5L11.0013 1.5"
            stroke="#006AFF"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
        </svg>
      </button>
      <div
        v-else
        class="button button-fill-blue"
        style="border-radius: 3.1px"
      >
        <p>
          {{ index + 1 }}
        </p>
      </div>
      <span
        class="m-l-7 f-size-5 text-capitalize text-medium"
        :class="{ grey: index > stepCount }"
      >
        {{ step }}
      </span>
    </button>
  </div>
</template>

<script>
export default {
  name: "StepNavigation",
  props: {
    stepCount: {
      type: Number,
      default: 0,
      validator: (propValue) => {
        const validProp = propValue <= 2 && propValue >= 0;
        return validProp;
      },
    },
    disabled: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      steps: ["verify account", "social handles", "business category"],
    };
  },
  methods: {
    moveToStep(index) {
      if (index === 0 || (index && !this.disabled[index - 1].isDisabled)) {
        this.$emit("stepper", index);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
button {
  border: none;
  background: none;
  cursor: pointer;
}

.grey {
  color: rgba(165, 180, 203, 1);
  cursor: not-allowed;
}

.grey-bg {
  background: rgba(228, 233, 239, 1);
}

</style>

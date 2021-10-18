<template>
  <div
    class="custom-select"
    :tabindex="tabindex"
    @blur="open = false"
  >
    <div
      class="selected d-flex items-center justify-between"
      :class="{open: open}"
      @click="open = !open"
    >
      {{ selected }}
    </div>
    <div
      class="items"
      :class="{selectHide: !open}"
    >
      <div
        class="item"
        v-for="(option, i) of options"
        :key="i"
        @click="selected=option; open=false; $emit('input', option)"
      >
        {{ option }}
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props:{
    options:{
      type: Array,
      required: true
    },
    tabindex:{
      type: Number,
      required: false,
      default: 0
    }
  },
  data() {
    return {
      selected: this.options.length > 0 ? this.options[0] : null,
      open: false
    };
  },
  mounted(){
    this.$emit('input', this.selected);
  }
};
</script>

<style scoped>

.custom-select {
  position: relative;
  width: 100%;
  text-align: left;
  outline: none;
  height: 54px;
  line-height: 47px;
  margin: 8px 0;
}

.selected {
  background-color: #fff;
  border-radius: 6px;
  border: 1px solid #E4E9EF;
  color: #000;
  padding-left: 8px;
  cursor: pointer;
  user-select: none;
  height: 100%;
}

.selected.open{
  border: 1px solid #E4E9EF;
  border-radius: 6px 6px 0px 0px;
}

.selected:after {
  position: absolute;
  content: "";
  top: 22px;
  right: 10px;
  width: 0;
  height: 0;
  border: 4px solid transparent;
  border-color: #A5B4CB transparent transparent transparent;
}

.items {
  color: #fff;
  border-radius: 0px 0px 6px 6px;
  overflow: hidden;
  position: absolute;
  background-color:  #5257F5;
  left: 0;
  right: 0;
}

.item{
  color: #ffffff;
  padding-left: 8px;
  cursor: pointer;
  user-select: none;
}

.item:hover{
  background-color: #7eaaec;
  color: #fff;
}

.selectHide {
  display: none;
}
</style>
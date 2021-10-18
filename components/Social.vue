<template>
  <div>
    <div class="m-b-25 m-t-25">
      <h2 class="f-size-7">Social Handles</h2>
      <p class="f-size-3 text-medium m-b-4">
        Enter your business social media handles
      </p>
    </div>
    <div>
      <div class="col-6 m-r-10">
        <label for="abeg_tag">Choose your Abeg Tag (required)</label>
        <input type="text" value="@" />
      </div>
      <div class="d-flex items-center col-12">
        <div class="col-6 m-r-8">
          <label for="abeg_tag">Instagram</label>
          <input type="text" value="@" />
        </div>
        <div class="col-6 m-l-8">
          <label for="abeg_tag">Twitter</label>
          <input type="text" value="@" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Social",
};
</script>

<style lang="scss" scoped>
p {
  color: #7d8da7;
}
</style>
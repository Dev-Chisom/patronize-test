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
        <label for="abeg_tag" class="m-b-3"
          >Choose your Abeg Tag (required)</label
        >
        <input type="text" value="@" />
      </div>
      <div class="d-flex items-center col-12 m-t-10 m-b-18 desktop-input">
        <div class="col-6 m-r-8">
          <label for="abeg_tag" class="m-b-3">Instagram</label>
          <input type="text" value="@" />
        </div>
        <div class="col-6 m-l-8">
          <label for="abeg_tag" class="m-b-3">Twitter</label>
          <input type="text" value="@" />
        </div>
      </div>
    </div>
    <hr class="m-t-28" />
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
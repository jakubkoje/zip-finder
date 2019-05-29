<template>
  <ion-grid>
    <form @submit="onSubmit">
      <ion-col>
        <ion-item>
          <ion-label>Zipcode:</ion-label>
          <ion-input
            :value="zip"
            @input="zip = $event.target.value"
            placeholder="Enter Slovak Zipcode"
          ></ion-input>
        </ion-item>
      </ion-col>
      <ion-col>
        <ion-button type="submit" color="primary" expand="block">Find</ion-button>
      </ion-col>
    </form>
  </ion-grid>
</template>

<script>
export default {
  name: "ZipSearch",
  data() {
    return {
      zip: ""
    };
  },
  methods: {
    onSubmit(e) {
      this.$emit("search-zip", this.zip);
      e.preventDefault();
    }
  }
};
</script>

<style>
</style>

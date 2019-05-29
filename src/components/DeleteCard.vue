<template>
  <ion-button
    v-if="info"
    type="submit"
    color="primary"
    expand="block"
    @click="deleteCard"
  >Remove Zip Info</ion-button>
</template>

<script>
export default {
  name: "DeleteCard",
  props: ["info"],
  methods: {
    deleteCard() {
      this.$emit("delete-card");
    }
  }
};
</script>

<style>
</style>

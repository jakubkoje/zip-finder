<template>
  <div class="ion-page">
    <ion-header>
      <ion-toolbar>
        <ion-title>ZipInfo</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <ZipSearch @search-zip="findInfo"/>
      <ZipCard :info="info"/>
      <DeleteCard :info="info" @delete-card="deleteCard"/>
    </ion-content>
  </div>
</template>

<script>
import ZipSearch from "../components/ZipSearch";
import ZipCard from "../components/ZipCard";
import DeleteCard from "../components/DeleteCard";
export default {
  name: "home",
  components: {
    ZipSearch,
    ZipCard,
    DeleteCard
  },
  data() {
    return {
      info: ""
    };
  },
  methods: {
    async findInfo(zip) {
      zip = zip.replace(/\s/g, "");
      zip = zip.slice(0, 3) + " " + zip.slice(3);
      const res = await fetch(`https://api.zippopotam.us/SK/${zip}`);
      if (res.status == 404) {
        this.showAlert();
      } else {
        this.info = await res.json();
        this.card = true;
      }
      console.log(this.info);
    },
    deleteCard() {
      this.info = "";
    },
    showAlert() {
      return this.$ionic.alertController
        .create({
          header: "Not Valid",
          message: "Please enter a valid Slovak zipcode",
          buttons: ["OK"]
        })
        .then(a => a.present());
    }
  }
};
</script>

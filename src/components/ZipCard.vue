<template>
  <ion-card v-if="info">
    <ion-card-header>
      <ion-card-subtitle>{{info["post code"]}}</ion-card-subtitle>
      <ion-card-title v-for="(place, index) in info.places" :key="index">{{place["place name"]}}</ion-card-title>
    </ion-card-header>

    <ion-card-conte>
      <ion-list>
        <ion-item>
          <ion-label>
            <strong>State:</strong>
            {{info.country}} ({{info["country abbreviation"]}})
          </ion-label>
        </ion-item>
      </ion-list>
    </ion-card-conte>
  </ion-card>
</template>

<script>
export default {
  name: "ZipCard",
  props: ["info"]
};
</script>

<style>
</style>

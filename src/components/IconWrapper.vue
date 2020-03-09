<template>
  <div class="icon-wrapper">
    <div class="icon-styles" v-bind:style="{
    'background-image': 'url(' + iconUrl + ')'}"></div>
    <p>{{icon.label}}</p>
  </div>
</template>

<script>
export default {
  name: "IconWrapper",
  props: {
    icon: Object,
    isHighResScreen: Boolean
  },
  computed: {
    iconUrl: function() {
      if (this.$props.isHighResScreen) {
        return require(`../assets/${this.$props.icon.iconName}@2x.png`);
      }
      return require(`../assets/${this.$props.icon.iconName}.png`);
    }
  }
};
</script>

<style lang="scss">
div.icon-wrapper {
  width: 80px;
  margin-left: calc(25% - 40px);
  margin-right: calc(25% - 40px);
  margin-bottom: 16px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;

  @media (min-width: 500px) {
    margin-left: calc(12.5% - 40px);
    margin-right: calc(12.5% - 40px);
  }

  @media (min-width: 1000px) {
    margin-left: calc(8.33% - 40px);
    margin-right: calc(8.33% - 40px);
  }

  div.icon-styles {
    background-size: 80px;
    width: 80px;
    height: 80px;
  }

  p {
    color: white;
  }
}
</style>

<template>
  <div
    id="app"
    :class="{ 'starry-night': isStarryNight, 'yin-yang': isYinYang, 'polka-dot': isPolkaDot, 'cicada-stripes': isCicadaStripes }"
  >
    <draggable class="draggable" v-model="icons" group="icons" @start="drag=true" @end="drag=false">
      <IconWrapper
        v-for="(icon, index) of icons"
        :key="index"
        :icon="icon"
        :isHighResScreen="isHighResScreen"
      />
    </draggable>
    <div class="draggable">
      <div
        class="icon-wrapper background-selector"
        v-for="(selector, index) of selectors"
        @click="setBackground"
        :key="index"
      >
        <div class="icon-styles" :class="selector.className"></div>
        <p>Select Background {{selector.pattern}}</p>
      </div>
    </div>
  </div>
</template>

<script>
import IconWrapper from "./components/IconWrapper";
import draggable from "vuedraggable";
import "./index.css";

export default {
  name: "App",
  components: {
    IconWrapper,
    draggable
  },
  data() {
    return {
      isStarryNight: true,
      isYinYang: false,
      isPolkaDot: false,
      isCicadaStripes: false,
      selectors: [
        {
          pattern: "Starry Night",
          className: "starry-night"
        },
        {
          pattern: "Yin Yang",
          className: "yin-yang"
        },
        {
          pattern: "Polka Dot",
          className: "polka-dot"
        },
        {
          pattern: "Cicada Stripes",
          className: "cicada-stripes"
        }
      ],
      isHighResScreen: window.devicePixelRatio > 1,
      icons: [
        {
          label: "label 1",
          iconName: "001"
        },
        {
          label: "label 2",
          iconName: "002"
        },
        {
          label: "label 3",
          iconName: "003"
        },
        {
          label: "label 4",
          iconName: "004"
        },
        {
          label: "label 5",
          iconName: "005"
        },
        {
          label: "label 6",
          iconName: "006"
        },
        {
          label: "label 7",
          iconName: "007"
        },
        {
          label: "label 8",
          iconName: "008"
        },
        {
          label: "label 9",
          iconName: "009"
        },
        {
          label: "label 10",
          iconName: "010"
        },
        {
          label: "label 11",
          iconName: "011"
        },
        {
          label: "label 12",
          iconName: "012"
        }
      ]
    };
  },
  methods: {
    setBackground: function(event) {
      this.isStarryNight = false;
      this.isYinYang = false;
      this.isPolkaDot = false;
      this.isCicadaStripes = false;

      switch (event.target.classList[1]) {
        case "starry-night":
          this.isStarryNight = true;
          break;
        case "yin-yang":
          this.isYinYang = true;
          break;
        case "polka-dot":
          this.isPolkaDot = true;
          break;
        case "cicada-stripes":
          this.isCicadaStripes = true;
          break;
      }
    }
  }
};
</script>

<style scoped lang="scss">
#app {
  height: 100vh;

  div.draggable {
    display: flex;
    flex-wrap: wrap;

    div.background-selector {
      div.icon-styles {
        border-radius: 50%;
      }
    }
  }
}
</style>

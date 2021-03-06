<template>
  <div :class="`parallaxCard  ${containerClass}`">
    <div class="parallaxFront" :style="{ 'background-color' : backgroundColor }">
      <svg-icon v-if="icon" :src="icon"></svg-icon>
    </div>
    <div class="parallaxBack">
      <div class="header">{{ title }}</div>
      <markdown-renderer class="description" :source="description"></markdown-renderer>
    </div>
  </div>
</template>

<script>
import MarkdownRenderer from "./MarkdownRenderer";
import SvgIcon from "./SVGIcon";

export default {
  name: "ParallaxCard",
  props: [
    "backgroundColor",
    "icon",
    "index",
    "title",
    "description",
    "isFile",
    "containerClass"
  ],
  components: {
    SvgIcon,
    MarkdownRenderer
  }
};
</script>

<style lang="scss">
@import "../assets/global.scss";

.parallaxCard {
  transform-style: preserve-3d;
  perspective: 1000px;
  transform: rotate(0deg);
  z-index: 99;
  position: relative;
  width: 100%;
  padding-top: 100%;
  transition: transform 0.7s cubic-bezier(0.4, 0.2, 0.2, 1);

  &:hover {
    transform: rotateY(180deg);
  }

  .parallaxFront,
  .parallaxBack {
    position: absolute;
    backface-visibility: hidden;
    width: 100%;
    height: 100%;
    transform-style: preserve-3d;
    top: 0;
  }

  .parallaxFront {
    z-index: 100;
    justify-content: center;
    align-items: center;
    display: flex;

    .iconContainer {
      transform-style: preserve-3d;
      transform: translateZ(80px);
      display: flex;
      justify-content: center;

      svg {
        width: 50%;
        fill: #fff;
        color: #fff;
      }
    }
  }

  .parallaxBack {
    background: lighten($primaryGrey, 15%);
    transform: rotateY(180deg);
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 5%;

    .header {
      color: #fff;
      font-size: 28px;
      transform-style: preserve-3d;
      transform: translateZ(80px);
      padding-bottom: 20px;
    }

    .description {
      color: #e9e9e9;
      font-size: 18px;
      width: 100%;
      transform-style: preserve-3d;
      transform: translateZ(75px);
    }

    @include tablet {
      .header {
        font-size: 36px;
      }

      .description {
        font-size: 24px;
      }
    }

    @include desktop {
      .header {
        font-size: 28px;
      }

      .description {
        font-size: 18px;
      }
    }
  }
}
</style>



<template>
  <div class="portfolio">
    <hero-header :backgroundImage="heroImage" heroButtonScrollTo="#portfolioContainer">
      <div class="title enter-1" slot="title">
        <h2>The Name's Watson.</h2>
        <h2>
          <span class="highlight">Conor Watson.</span>
        </h2>
      </div>
      <div class="subtitle enter-2" slot="subtitle">
        <span>I am a Full Stack Developer with&nbsp;</span>
        <div class="subtitleWords">
          <span class="highlight">a passion for problem solving.</span>
          <span class="highlight">an eye for design.</span>
          <span
            class="highlight"
          >a love for creating Web Apps with more features than a Bond gadget.</span>
          <span class="highlight">the knack of picking up new skills quickly.</span>
          <span class="highlight">the most handsome dog in the world.</span>
        </div>
      </div>
    </hero-header>
    <portfolio-list></portfolio-list>
    <web-footer></web-footer>
  </div>
</template>

<script>
// @ is an alias to /src
import PortfolioList from "../components/PortfolioList";
import HeroHeader from "../components/HeroHeader";
import PortfolioImage from "../assets/hero-header/Home-Header.jpg";
import WebFooter from "../components/Footer";

export default {
  name: "portfolio",
  components: {
    PortfolioList,
    HeroHeader,
    WebFooter
  },
  data() {
    return {
      heroImage: PortfolioImage
    };
  },
  beforeRouteUpdate(to, from, next) {
    if (from.name === "portfolioItem") {
      const closeButton = this.$el.querySelector(".closeButton");
      if (closeButton) closeButton.click();
      setTimeout(() => {
        next();
      }, 650);
    } else {
      next();
    }
  }
};
</script>

<style lang="scss">
@import "../assets/global.scss";

.portfolio {
  .heroImage {
    .title {
      margin-top: 50px;
      margin-bottom: 225px;

      h2 {
        font-size: 42px;
        margin: 0;
      }
    }

    .subtitle {
      font-size: 20px;
    }
  }

  @include tablet {
    .heroImage {
      .title {
        margin-bottom: 150px;

        h2 {
          font-size: 52px;
        }
      }

      .subtitle {
        font-size: 24px;
      }
    }
  }

  @include desktop {
    .heroImage {
      .title {
        h2 {
          font-size: 68px;
        }
      }

      .subtitle {
        font-size: 24px;
      }
    }
  }

  .subtitleWords {
    //height: 50px;
    margin-top: 15px;
    position: relative;
    width: 100%;
    margin-bottom: 100px;

    @include desktop {
      margin-bottom: 0;
    }

    span {
      display: block;
      position: absolute;
      width: 100%;
      opacity: 0;
      overflow: hidden;
      text-align: center;
      animation: rotateWords 20s linear infinite 0s;

      &:nth-child(2) {
        animation-delay: 4s;
      }
      &:nth-child(3) {
        animation-delay: 8s;
      }
      &:nth-child(4) {
        animation-delay: 12s;
      }
      &:nth-child(5) {
        animation-delay: 16s;
      }
      &:nth-child(6) {
        animation-delay: 20s;
      }
    }
  }

  @keyframes rotateWords {
    0% {
      opacity: 0;
    }
    2% {
      opacity: 0;
      -webkit-transform: translateY(-30px);
      transform: translateY(-30px);
    }
    8% {
      opacity: 1;
      -webkit-transform: translateY(0px);
      transform: translateY(0px);
    }
    18% {
      opacity: 1;
      -webkit-transform: translateY(0px);
      transform: translateY(0px);
    }
    22% {
      opacity: 0;
      -webkit-transform: translateY(30px);
      transform: translateY(30px);
    }
    80% {
      opacity: 0;
    }
    100% {
      opacity: 0;
    }
  }
}
</style>


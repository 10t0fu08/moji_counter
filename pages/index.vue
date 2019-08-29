<template>
  <div class="wrapper">
    <Header />
    <div class="pr-wrapper">
      <progress class="progress" v-bind:value="percentage" v-bind:max="100"></progress>
      <p class="percentage">{{percentageText}}%</p>
    </div>
    <div class="goal-wrapper">
      <p class="goal-text">Goal :</p>
      <input type="number" class="counter" step="100" min="0" max="9999" v-model="counter" />
      <p class="moji">moji</p>
    </div>
    <p class="now">
      now :
      <span>{{textCount}}</span>
    </p>
    <div>
      <textarea name id cols="30" rows="10" v-model.trim="text"></textarea>
    </div>
    <Footer class="footer" />
  </div>
</template>

<script>
import Header from "~/components/header.vue";
import Footer from "~/components/footer.vue";

export default {
  components: {
    Header,
    Footer
  },
  data: function() {
    return {
      counter: 100,
      text: ""
    };
  },

  computed: {
    textCount: function() {
      return this.text.length;
    },

    percentage: function() {
      if (this.counter === "0") {
        return 0;
      } else {
        return (this.textCount / this.counter) * 100;
      }
    },
    percentageText: function() {
      if (this.counter === "0") {
        return "0";
      } else {
        return Math.floor(this.percentage);
      }
    }
  },
  mounted: function() {
    if (localStorage.text) {
      this.text = localStorage.text;
    }
    if (localStorage.counter) {
      this.counter = localStorage.counter;
    }
  },
  watch: {
    text(newText) {
      localStorage.text = newText;
    },
    counter(newCounter) {
      localStorage.counter = newCounter;
    }
  }
};
</script>
<style lang="scss">
.pr-wrapper {
  position: relative;
  .progress {
    width: 100%;
    height: 2rem;
    margin: auto;
    z-index: 0;
  }
  .percentage {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 1;
    font-size: 1.6rem;
    font-weight: bold;
    color: #ececec;
    background: none;
  }
}
.goal-wrapper {
  display: flex;
  margin-left: 11.2rem;
  margin-top: 2.4rem;
  .goal-text {
    font-size: 1.8rem;
    font-weight: bold;
    margin-right: 0.4em;
    line-height: 3.2rem;
    color: #ececec;
    margin-bottom: 0;
  }
  .counter {
    width: 8.4rem;
    height: 3.2rem;
    font-size: 2rem;
    font-weight: bold;
    border: 2px solid #ececec;
    border-radius: 0.4em;
    padding-left: 0.4em;
    color: #ececec;
  }
}
@media screen and (max-width: 960px) {
  .goal-wrapper {
    margin-left: 4rem;
  }
}
@media screen and (max-width: 770px) {
  .goal-wrapper {
    margin-left: 2rem;
  }
}
.now {
  color: #ececec;
  margin-top: 2.4rem;
  margin-left: 11.2rem;
  font-size: 2rem;
  font-weight: bold;
  span {
    font-size: 2.4rem;
    font-weight: bold;
  }
}
@media screen and (max-width: 960px) {
  .now {
    margin-left: 4rem;
  }
}
@media screen and (max-width: 770px) {
  .now {
    margin-left: 2rem;
  }
}
textarea {
  display: block;
  width: 85%;
  height: 60vh;
  margin: auto;
  box-sizing: border-box;
  margin-top: 2.4rem;
  color: #ececec;
  font-size: 2.4rem;
  font-weight: bold;
  padding: 1em;
  border: 2px solid #ececec;
  border-radius: 1.2em;
  resize: none;
}
@media screen and (max-width: 960px) {
  textarea {
    width: 92%;
  }
}

.footer {
  margin-top: 2.4rem;
}
</style>

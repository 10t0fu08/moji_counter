<template>
  <div class="header">
    <p class="title">moji counter</p>
  </div>
</template>

<style lang="scss">
.header {
  background-color: #282828;
  color: #ececec;
  width: 100%;
  height: 6.4rem;
  box-shadow: 0 3px 12px rgba(0, 0, 0, 0.16);
  display: flex;
  z-index: 1000;

  .title {
    font-size: 2.8rem;
    line-height: 6.4rem;
    margin: 0;
    margin-left: 4em;
    font-weight: bold;
  }

  @media screen and (max-width: 960px) {
    .title {
      font-size: 2rem;
      margin-left: 2em;
    }
  }

  @media screen and (max-width: 770px) {
    .title {
      margin: auto;
      line-height: 6.4rem;
    }
  }
}
</style>
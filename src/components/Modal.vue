<template>
  <div class="modal">
    <div class="modal-content">
      <div class="logo">newsDev</div>
      <img :src="item.links[0].href" :alt="item.data[0].title">
      <h1> {{ item.data[0].title }} </h1>
      <p v-html="item.data[0].description"></p>
      <div class="close" @click="$emit('close')">
        <div class="bar1"></div>
        <div class="bar2"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    item: Object,
  },
  data() {
    return {
      text: null,
    };
  },
};
</script>

<style lang="scss" scoped>
  .modal {
    z-index: 10;
    width: 100%;
    height: 100vh;
    position: fixed;
    top: 0;
    left: 0;
    background: rgba(#000, .7);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    .modal-content {
      position: relative;
      background: white;
      padding: 5vh;
      padding-right: 7.5vh;
      width: 60%;
      height: 60vh;
      overflow: hidden;

      .logo {
        position: absolute;
        top: 0;
        left: 0;
        padding: 2.5vh;
        color: black;
        font-size: 25px;
      }

      img {
        float: left;
        width: 60vh;
        height: 100%;
        padding-right: 5%;
      }

      p {
        margin-top: 1%;
        width: 47.5vh;
        height: 40vh;
        overflow: scroll;
        overflow-x: hidden;
        whitespace: nowrap;
        text-overflow: ellipsis;
        padding-right: 17px;
        text-indent: 5%;
        text-align: justify;

        /deep/ a {
          color: #1a6;
          text-decoration: none;
          font-weight: bold;
        }

        /deep/ b {
          font-weight: normal;
        }
      }

      .close {
        position: absolute;
        right: 0;
        top: 0;
        width: 5vh;
        height: 5vh;
        margin: 2.5vh;
        transition: .3;

        .bar1, .bar2 {
          position: absolute;
          width: 100%;
          height: 15%;
          background: black;
          margin-top: 20%;
        }

        .bar1 {
          transform: rotate(45deg);
        }
        .bar2 {
          transform: rotate(-45deg);
        }

        &:hover {
          cursor: pointer;

          .bar1, .bar2 {
            background: #1a6;
          }
        }
      }
    }
  }

  @media all and (min-width: 992px) and (max-width: 1200px) {
    .modal {
      width: 100%;
      height: 100vh;
      background: white;

      .modal-content {
        width: 100%;
        height: 100%;
        padding: 5%;
        padding-right: 5%;
        padding-top: 15%;

        img {
          width: 100%;
          height: 40vh;
        }

        h1 {
          font-size: 50px;
          text-align: center;
        }

        p {
          font-size: 30px;
          text-align: justify;
          width: 100%;
        }
      }
    }
  }

  @media all and (max-width: 1200px) {
    .modal {
      width: 100%;
      height: 100vh;
      background: white;

      .modal-content {
        width: 100%;
        height: 100%;
        padding: 5%;
        padding-top: 15%;

        img {
          width: 100%;
          height: 40vh;
        }

        h1 {
          text-align: center;
        }

        p {
          text-align: justify;
          width: 100%;
        }
      }
    }
  }
</style>

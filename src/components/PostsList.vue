<template>
  <div  class="container">
    <h1>newsDev</h1>
    <ul>
      <li @click="showModal(item)" v-for="item in items" :key="item.data[0].nasa_id">
        <img :src="item.links[0].href" :alt="item.data[0].title" >
        <div class="after">
          <i class="fas fa-search"></i>
        </div>
      </li>
    </ul>
    <Modal @close="closeModal" :item="item" v-show="isModalVisible" />
  </div>
</template>

<script>
import axios from 'axios';
import Modal from './Modal.vue';

export default {
  name: 'PostsList',
  components: {
    Modal,
  },
  data() {
    return {
      items: null,
      isModalVisible: false,
      item: null,
    };
  },
  mounted() {
    axios
      .get('https://images-api.nasa.gov/search?q=moon&media_type=image')
      .then((resp) => {
        this.items = resp.data.collection.items;
      });
  },
  methods: {
    showModal(item) {
      this.isModalVisible = true;
      const name = item.data[0].title;
      this.item = item;
      console.log(name);
    },
    closeModal() {
      this.isModalVisible = false;
    },
  },
};
</script>

<style scoped lang="scss">
.container {
  color: black;
  width: 100%;
}
h1 {
  color: darken(#1a6, 20%);
  font-size: 45px;
  width: 100%;
  text-align: center;
  position: fixed;
  z-index: 5;
  top: 0px;
  background: rgba(#fff, .8);
}
ul {
  position: absolute;
  list-style-type: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
  margin-top: 15%;
  justify-content: center;
  li {
    position: relative;
    width: 40vh;
    height: 40vh;
    margin: 2vh;
    overflow: hidden;
    img {
      z-index: 1;
      width: 100%;
      height: 100%;
    }

    .after {
      position: absolute;
      top:  100%;
      z-index: 2;
      width: 100% ;
      height: 100%;
      transition: .3s;
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 35px;
    }

    &:hover {
      cursor: pointer;
    }

    &:hover .after {
      top: 0%;
      transform: scale(1.02);
      background: rgba(72, 170, 15, .8);
    }

    a {
      color: #1a6;
    }
  }
}

</style>

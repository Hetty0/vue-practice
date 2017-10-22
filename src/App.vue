<template>
  <div class="page">
    <!-- <img src="./assets/img1.png"> -->
    <div class="single-card" v-for="item in blogData" track-by="$index">
      <card :card-data="item"></card>
    </div>
    <div class="add-btn" @click="addCard">
      <span class="add">+</span>
      <span class="text"> Add New</span>
    </div>
    <template-blog v-show="isAddNew"></template-blog>
  </div>
</template>

<script>
  import blogData from './config';
  import card from 'components/card/card';
  import templateBlog from 'components/template-blog/template-blog';

  export default {
    components: {
      card,
      templateBlog
    },
    data () {
      return {
        blogData: blogData,
        isAddNew: false,
        title: 'Edit'
      };
    },
    methods: {
      addCard () {
        this.isAddNew = true;
      }
    },
    events: {
      hideBlog () {
        this.isAddNew = false;
      }
    }
  };
</script>

<style lang="less">
  .page {
    position: relative;
    padding: 40px 196px 20px 42px;
    .add-btn {
      position: absolute;
      top: 40px;
      left: 484px;
      width: 110px;
      height: 30px;
      line-height: 30px;
      text-align: center;
      border-radius: 2px;
      background-color: #5fb485;
      color: #ffffff;
      cursor: pointer;
      span {
        font-weight: bold;
      }
      .add {
        vertical-align: top;
      }
      .text {
        vertical-align: middle;
      }
    }
  }
</style>

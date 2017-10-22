<template>
  <div class="card-wrapper" @mouseenter="enterCard" @mouseleave="leaveCard">
    <div class="card-img">
      <img :src="cardData.imgSrc">
    </div>
    <h1 class="card-title">{{ cardData.title }}</h1>
    <p class="card-text">{{ cardData.text }}</p>
    <div class="edit-btn" v-show="isEdit" @click="editCard">Edit</div>
    <template-blog v-show="showEditCard" :title="edit" :card-data="cardData"></template-blog>
  </div>
</template>

<script>
  import templateBlog from 'components/template-blog/template-blog';
  
  export default {
    props: {
      cardData: {
        type: Object
      }
    },
    components: {
      templateBlog
    },
    data () {
      return {
        isEdit: false,
        showEditCard: false,
        edit: 'Edit Article'
      };
    },
    methods: {
      enterCard () {
        this.isEdit = true;
      },
      leaveCard () {
        this.isEdit = false;
      },
      editCard () {
        this.showEditCard = true;
      }
    },
    events: {
      hideBlog () {
        this.showEditCard = false;
      }
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" rel="stylesheet/less" scoped>
  .card-wrapper {
    position: relative;
    width: 396px;
    box-sizing: border-box;
    border: 1px solid #dadada;
    background-color: #ffffff;
    margin-bottom: 20px;
    padding: 14px 14px 0 14px;
    .card-img {
      width: 366px;
      height: 244px;
      img {
        width: 100%;
        height: 100%;
      }
    }
    .card-title {
      margin-top: 12px;
      line-height: 26px;
      font-size: 14px;
    }
    .card-text {
      width: 120%;
      line-height: 20px;
      font-size: 10px;
      -webkit-text-size-adjust: none;
      -webkit-transform: translate(-10%, -10%) scale(0.8);
    }
    .edit-btn {
      position: absolute;
      top: 0;
      right: 0;
      width: 68px;
      height: 36px;
      line-height: 36px;
      text-align: center;
      border-radius: 2px;
      background-color: rgba(0, 0, 0, 0.5);
      color: #ffffff;
      cursor: pointer;
    }
  }
</style>

<template>
  <div class="template-wrapper">
    <div class="mask"></div>
    <div class="card">
      <h1 class="title">{{title}}</h1>
      <div class="item">
        <h3 class="info">Image</h3>
        <input type="text" :value="cardData.imgSrc">
      </div>
      <div class="item">
        <h3 class="info">Title</h3>
        <input type="text" :value="cardData.title">
      </div>
      <div class="item">
        <h3 class="info">Content</h3>
        <textarea :value="cardData.text"></textarea>
      </div>
      <div class="btn-wrapper">
        <div class="cancel btn" @click="cancel">Cancel</div>
        <div class="save btn">Save</div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      title: {
        type: String,
        default: 'Add Article'
      },
      cardData: {
        type: Object,
        default () {
          return {
            title: '',
            imgSrc: '',
            text: ''
          };
        }
      }
    },
    data () {
      return {
        isBlogShow: false
      };
    },
    methods: {
      hideBlog () {
        this.$dispatch('hideBlog');
      },
      cancel () {
        this.hideBlog();
      }
    }
  };
</script>

<style lang="less" scoped>
  .template-wrapper {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 100;
    width: 100%;
    height: 100%;
    .mask {
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.2);
    }
    .card {
      position: absolute;
      top: 50%;
      left: 50%;
      width: 384px;
      height: 368px;
      box-sizing: border-box;
      padding: 24px 24px 18px 24px;
      transform: translate(-50%, -50%);
      background-color: #ffffff;
      .title {
        font-weight: bold;
        margin-bottom: 12px;
      }
      .item {
        margin-bottom: 6px;
      }
      .info {
        line-height: 26px;
      }
      input, textarea {
        width: 100%;
        border: 2px solid #e8e8e8;
      }
      input {
        height: 28px;
      }
      textarea {
        height: 80px;
      }
      .btn-wrapper {
        display: flex;
        flex-direction: row-reverse;
        margin-top: 18px;
        .btn {
          width: 78px;
          height: 28px;
          line-height: 28px;
          text-align: center;
          font-weight: bold;
        }
      }
      .save {
        background-color: #328557;
        color: #ffffff;
      }
      .cancel {
        color: #b4b4b4;
      }
    }
  }
</style>



<template>
  <div class="tar-bar-item">
    <div @click="itemClick" v-if="!isActive"><slot name="item-icon"></slot></div>
    <div v-else><slot name="item-icon-active"></slot></div>
    <!-- <div :class="{active: isAcitve}"><slot name="item-text"></slot></div> -->
    <div :style="activeStyle"><slot name="item-text"></slot></div>
  </div>
</template>

<script>
export default {
  name: 'TabBarItem',
  props: {
    path:String,
    activeColor: {
      type: String,
      default: 'red'
    }
  },
  data() {
    return {
      // isAcitve: false
    }
  },
  computed: {
    isActive() {
      //  /home -> item(/home) = true
      //  /home -> item(/category) = false
      //  /home -> item(/cart) = false
      //  /home -> item(/profile) = false
      return this.$route.path.indexOf(this.path) !== -1
    },
    activeStyle() {
      return this.isActive ? {color: this.activeColor} : {}
    }
  },
  methods: {
    itemClick() {
      // console.log('itemClick');
      this.$router.replace(this.path)
    }
  }
}
</script>>

<style scoped>
  
  .tar-bar-item {
    flex: 1;
    text-align: center;
    height: 49px;
    font-size: 14px;
  }

  .tar-bar-item img {
    width: 24px;
    height: 24px;
    margin-top: 3px;
    vertical-align: middle;
    margin-bottom: 2px;
  }

  .active{
    color: red;
  }

</style>
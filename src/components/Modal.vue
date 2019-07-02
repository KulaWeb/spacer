<template>
    <div class="outerWrapper">
        <div class="innerWrapper">
            <div class="photo">
                <img :src="photo" alt="" />
            </div>
            <div class="description">
                <h2 class="title"> {{ title }} </h2>
                <p class="description">{{ description }}</p>
            </div>
            <div class="close" @click="$emit('closeModal')"></div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      photo: null,
      title: null,
      description: null,
    };
  },
  mounted() {
    this.photo = this.item.links[0].href;
    this.title = this.item.data[0].title;
    this.description = this.item.data[0].description;
  },
};
</script>

<style lang="scss" scoped>
.outerWrapper {
    background-color: #fff;
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    z-index: 999;
}

.close {
    position: absolute;
    width: 30px;
    height:  30px;
    padding: 30px;
    top: 0;
    right: 0;
    cursor: pointer;
    z-index: 999;
    &:after, &:before {
        content: '';
        position: absolute;
        top: 30px;
        right: 20px;
        width: 20px;
        height: 2px;
        background-color: black;
        display: block;
    }
    &:before {
        transform: rotate(45deg);
    }
    &:after {
        transform: rotate(-45deg);
    }
}
    .innerWrapper {
        display: flex;
        height: 100%;
        padding: 50px;
        justify-content: center;
        align-items: center;
        flex-direction: column;

        .photo {
            width: 100%;
        }
    }
</style>

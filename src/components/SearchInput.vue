<template>

        <input name="search"
               id="search"
               type="search"
               :class="{ dark }"
               :value="value"
               @input="handleChange"
        />

<!--    <ul>
        <li v-for="item in results" :key="item.data[0].nasa_id">
            {{ item.data[0].description}}
        </li>
    </ul>-->
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    value: {
      type: String,
      required: true,
    },
    dark: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
    input {
            display: flex;
            flex-direction: column;
            width: 250px;
            margin-top: 50px;
            border: 0;
            border-bottom: 2px solid #fff;
            color: #fff;
            font-size: 16px;
            font-weight: 400;
            text-align: center;
            height: 30px;
            background: none;
            transition: box-shadow .5s;
            &:focus {
                outline: none;
                box-shadow: 0 10px 20px -8px rgba(255, 255, 255, .3);
            }
        }
    .dark {
        border-color: black;
        color: black;
        &:focus {
            box-shadow: 0 10px 20px -8px rgba(0, 0, 0, .3);
        }
    }
</style>

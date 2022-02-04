<template>
  <form action="#" class="base-search">
    <button class="base-search__button search">
      <BaseIcon
        class="base-search__button-icon"
        name="search"
        @click="$emit('search')"
      />
    </button>

    <keep-alive>
      <input
        ref="searchInput"
        class="base-search__input"
        type="text"
        name="search"
        placeholder="Поиск по товарам"
        v-model="inputValue"
      />
    </keep-alive>

    <button class="base-search__button close">
      <BaseIcon
        class="base-search__button-icon"
        name="close"
        @click="$emit('hide')"
      />
    </button>
  </form>
</template>

<script>
  import BaseIcon from '@/components/ui/BaseIcon';

  export default {
    name: 'BaseSearch',

    components: {
      BaseIcon,
    },

    data() {
      return {
        inputValue: '',
      };
    },

    mounted() {
      this.focusSearchInput();
    },

    methods: {
      focusSearchInput() {
        this.$refs.searchInput.focus();
      },
    },
  };
</script>

<style lang="scss" scoped>
  .base-search {
    display: flex;
    align-items: center;

    width: 100%;
    margin-left: 20px;
    margin-right: 25px;
    padding: 14px 30px;

    border-radius: 30px;

    box-shadow: 0px 0px 20px rgba(157, 157, 157, 0.25);

    &__input {
      flex-grow: 1;
      &::placeholder {
        color: $silver;
      }
    }
    &__button {
      color: $silver;

      &.search {
        width: 31px;
        height: 31px;
        margin-right: 20px;
      }

      &.search & {
        &-icon {
          width: 31px;
          height: 31px;
        }
      }

      &.close {
        width: 25px;
        height: 25px;
      }
      &.close & {
        //разобраться со стилями
        &-icon {
          width: 25px;
          height: 25px;
        }
      }
    }
  }
</style>

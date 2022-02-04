<template>
  <header class="header">
    <MainContainer class="header__container">
      <nav class="header__navigation">
        <router-link class="header__navigation-logo" to="/">
          <img src="@/assets/img/logotype.png" alt="logo" />
        </router-link>

        <ul v-show="!baseSearchVisible" class="header__navigation-list">
          <li><router-link to="/catalog">Каталог товаров</router-link></li>
          <li><router-link to="/blog">Блог</router-link></li>
          <li><router-link to="/contacts">Контакты</router-link></li>
        </ul>

        <BaseSearch v-show="baseSearchVisible" @hide="hideBaseSearch" />

        <div class="header__navigation-group">
          <button
            v-show="!baseSearchVisible"
            class="header__navigation-button"
            @click="showBaseSearch"
          >
            <BaseIcon class="header__navigation-button-icon" name="search" />
          </button>

          <button class="header__navigation-button">
            <BaseIcon class="header__navigation-button-icon" name="basket" />
          </button>

          <button class="header__navigation-button">
            <BaseIcon class="header__navigation-button-icon" name="user" />
          </button>
        </div>
      </nav>
    </MainContainer>
  </header>
</template>

<script>
  import BaseIcon from '@/components/ui/BaseIcon';
  import BaseSearch from '@/components/ui/BaseSearch';
  import MainContainer from '@/components/containers/MainContainer';

  export default {
    name: 'TheHeader',

    components: {
      BaseIcon,
      BaseSearch,
      MainContainer,
    },

    data() {
      return {
        baseSearchVisible: false,
      };
    },

    methods: {
      showBaseSearch() {
        this.baseSearchVisible = !this.baseSearchVisible;
      },
      hideBaseSearch() {
        this.baseSearchVisible = false;
      },
    },
  };
</script>

<style lang="scss" scoped>
  .header {
    width: 100%;
    padding: 22px 0;

    box-shadow: 0px 5px 20px rgba(157, 157, 157, 0.25);

    &__navigation {
      display: flex;
      align-items: center;
      flex-grow: 1;
      justify-content: space-between;

      &-logo {
        display: inline-block;

        height: 116px;
      }

      &-list {
        @include text-nav-link;
        @include list-style-reset;

        display: flex;
        align-items: center;

        color: $cod-gray;

        & > {
          & :not(:first-child) {
            margin-left: 100px;
          }
        }
      }

      &-group {
        display: flex;
        align-items: center;
      }

      &-button {
        flex-grow: 1;

        color: $cod-gray;

        transition: all $transition-duration-normal ease;

        &:hover {
          color: $selective-yellow;
        }

        &:not(:first-child) {
          margin-left: 53px;
        }

        &-icon {
          width: 31px;
          height: 31px;
        }
      }
    }
  }
</style>

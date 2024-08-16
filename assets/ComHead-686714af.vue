<script setup lang="ts">
import SvgIcon from './SvgIcon.vue';
import { useRouter } from 'vue-router';
import { useStatusStore } from '@/stores/index';
const router = useRouter();
const useStatus = useStatusStore();

const routeTo = (url: string) => {
  router.push(url);
};

const closeMenu = () => {
  useStatus.menuOpen = false;
};

const popRoute = (url: string) => {
  window.open(url);
};

const menuList = [
  {
    title: 'PRIVACY',
    items: [
      {
        title: 'Terms of Use',
        url: '/terms.html',
        dotType: 'terms',
      },
      {
        title: 'Privacy Policy',
        url: '/privacy.html',
        dotType: 'privacy',
      },
    ],
  },
];
</script>

<template>
  <div class="header-component">
    <div class="header-component__container">
      <div class="header-component__logo" @click="routeTo('/')">
        <img
          class="header-component__logo-img"
          src="@/assets/img/logo.png"
          alt="logo"
        />
        <span class="header-component__logo-text">{{ $t('public') }}</span>
      </div>

      <div class="header-component__menu">
        <img
          src="@/assets/img/tools_icon.webp"
          :class="{ 'is-hidden': useStatus.menuOpen }"
          @click="useStatus.menuOpen = !useStatus.menuOpen"
        />
      </div>
    </div>
  </div>
  <Teleport to="#app">
    <div class="popup-component" :class="{ 'is-visible': useStatus.menuOpen }">
      <div
        class="popup-component__mask"
        v-if="useStatus.menuOpen"
        @click="useStatus.menuOpen = false"
      ></div>
      <div class="popup-component__main">
        <div class="popup-component__header">
          <img
            src="@/assets/img/tools_icon.webp"
            @click="useStatus.menuOpen = !useStatus.menuOpen"
          />
          <SvgIcon name="close" @click="closeMenu" />
        </div>
        <div class="popup-component__body">
          <div
            class="popup-component__menu-group"
            v-for="(item, index) in menuList"
            :key="index"
          >
            <h4 class="popup-component__menu-title">{{ item.title }}</h4>
            <nav class="popup-component__menu">
              <span
                @click="popRoute(linkItem.url)"
                class="popup-component__menu-item"
                v-for="(linkItem, li) in item.items"
                :key="li"
                >{{ linkItem.title }}</span
              >
            </nav>
          </div>
        </div>
      </div>
    </div>
  </Teleport>
</template>

<style lang="less">
.header-component {
  display: flex;
  width: 100%;
  height: auto;
  justify-content: center;
  box-sizing: border-box;
  padding: 22px 10px;
  position: absolute;
  top: 0;
  left: 50%;
  transform: translate(-50%, 0);
  z-index: 20;

  .header-component__container {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: #fff;
    line-height: 1;

    @media screen and (min-width: 769px) {
      max-width: 1200px;
    }
  }

  .header-component__logo {
    display: inline-flex;
    align-items: center;
    width: 24px;
    overflow: visible;
    white-space: nowrap;
    cursor: pointer;
  }

  .header-component__logo-img {
    width: 40px;
    height: 40px;
    margin-right: 16px;
  }

  .header-component__logo-text {
    font-size: 24px;
    font-weight: 600;
  }

  .header-component__menu {
    display: flex;
    align-items: center;
    position: relative;

    img {
      width: 24px;
      height: 24px;
      cursor: pointer;
    }
  }
}

.popup-component {
  position: absolute;
  top: 0;
  right: -100vw;
  z-index: 999;
  padding: 30px 20px 0;
  box-sizing: border-box;
  width: 410px;
  height: 100vh;
  display: flex;
  flex-direction: column;
  background: rgba(0, 0, 0, 0.8);
  border-radius: 0px 0px 0px 0px;
  transition: all 0.1s linear;

  &.is-visible {
    right: 0;
  }

  & > * {
    position: relative;
  }

  img {
    width: 24px;
    height: 24px;
    cursor: pointer;
  }

  .popup-component__mask {
    position: fixed;
    z-index: 0;
    width: 100vw;
    height: 100vh;
    left: 0;
    top: 0;
  }

  .popup-component__main {
    width: 100%;
    display: flex;
    flex-direction: column;

    .popup-component__header {
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 20px;
      color: #fff;
      line-height: 1;
    }

    .popup-component__body {
      width: 100%;
    }

    .popup-component__menu-group {
      display: flex;
      flex-direction: column;
      margin-top: 32px;
      line-height: 1;
    }

    .popup-component__menu-title {
      font-size: 20px;
      color: #fff;
    }

    .popup-component__menu {
      display: flex;
      flex-direction: column;
      box-sizing: border-box;
    }

    .popup-component__menu-item {
      font-size: 16px;
      transition: all linear 0.2s;
      text-decoration: none;
      margin-top: 24px;
      color: rgba(255, 255, 255, 0.9);
      word-spacing: 2px;
      cursor: pointer;

      &:hover {
        color: #2488ff;
      }
    }
  }
}

// @media screen and (max-width: 768px) {
//   .header-component {
//     padding: 16px 16px 8px;
//   }

//   .header-component__logo-img {
//     width: 32px;
//     height: 32px;
//     margin-right: 8px;
//   }

//   .header-component__logo-text {
//     font-size: 20px;
//   }

//   .popup-component {
//     padding: 16px 16px 0;
//     width: 70vw;
//     background-color: rgba(0, 0, 0, 0.9);

//     img {
//       width: 24px;
//       height: 24px;
//       cursor: pointer;
//     }
//   }

//   .popup-component__menu-item {
//     margin-top: 20px;

//     &:hover {
//       color: rgba(255, 255, 255, 0.8);
//     }
//   }

//   .popup-component__main {
//     .popup-component__menu-group {
//       margin-top: 1em;
//     }
//   }
// }
</style>
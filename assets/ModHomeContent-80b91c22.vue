<script setup lang="ts">
import { ComHead, ComCon, ModHomeList } from '@/components';
defineProps<{
  contents: number;
}>();

const contentBg = ['@/assets/img/home_bg_1.webp', '@/assets/img/home_bg_2.webp'];
</script>

<template>
  <ComCon :background="contentBg[contents]" is-full>
    <template v-if="contents === 0">
      <ComHead />
      <div class="content-main">
        <div class="content-main-left">
          <h1 class="content-main-left-title">{{ $t('homepage.title') }}</h1>
          <p
            class="content-main-left-subtitle"
            v-html="$t('homepage.desc')"
          ></p>
          <div class="btn-box">
            <span class="left-btn android" href="#" target="_blank"></span>
          </div>
        </div>
        <div class="content-main-right">
          <img class="content-main-right-img" src="@/assets/img/home_bg_2_1.webp" />
        </div>
      </div>
    </template>
    <template v-if="contents === 1">
      <div class="content-secondary">
        <div class="content-secondary-left">
          <img src="@/assets/img/home_bg_1_1.webp" />
        </div>
        <div class="content-secondary-right">
          <ModHomeList />
        </div>
      </div>
    </template>
  </ComCon>
</template>

<style lang="less" scoped>
.content-main {
  display: flex;
  justify-content: space-between;
  max-width: 1200px;
  margin: 0 auto;
  box-sizing: border-box;
  .content-main-left {
    width: 50%;
    color: #ffffff;
    font-weight: 500;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    .content-main-left-title {
      font-size: 64px;
      line-height: 75px;
    }
    .content-main-left-subtitle {
      font-size: 24px;
      line-height: 34px;
      margin: 20px 0 48px;
    }
    .btn-box {
      display: flex;
      align-items: center;
    }
    .left-btn {
      width: 215px;
      height: 64px;
      background: no-repeat center;
      background-size: cover;
      display: inline-block;
      &.android {
        margin-left: 20px;
        background-image: url('@/assets/img/google_pay.webp');
      }
    }
  }
  .content-main-right {
    width: 50%;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    justify-content: center;
  }
  .content-main-right-img {
    max-width: 100%;
    height: calc(637 / 942 * 100vh);
    max-height: 637px;
  }
}

.page-weather-loading {
  position: absolute;
  left: 50%;
  top: 100px;
  transform: translateX(-50%);
  display: flex;
  justify-content: center;
  .lottle-con {
    width: 40px;
    height: 40px;
    position: relative;
  }
  p {
    font-size: 24px;
    color: #2488ff;
    margin-left: 20px;
    margin-top: 4px;
  }
}

.content-secondary {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 1200px;
  margin: 0 auto;
  img {
    width: auto;
    height: calc(637 / 942 * 100vh);
    max-height: 637px;
    margin-left: -20px;
  }
}

// @media screen and (max-width: 768px) {
//   .content-main {
//     justify-content: center;
//     flex-direction: column-reverse;
//     align-items: center;
//     width: 100%;
//     padding-top: 80px;
//     .content-main-left {
//       width: 100%;
//       box-sizing: border-box;
//       display: flex;
//       flex-direction: column;
//       justify-content: center;
//       align-items: flex-start;
//       .content-main-left-title {
//         font-size: 32px;
//         line-height: 1;
//       }
//       .content-main-left-subtitle {
//         font-size: 16px;
//         line-height: 20px;
//         margin: 8px 0 24px;
//       }
//       .btn-box {
//         display: flex;
//         align-items: center;
//       }
//       .left-btn {
//         width: 120px;
//         height: 36px;
//         &.android {
//           margin-left: 8px;
//         }
//       }
//     }
//     .content-main-right {
//       width: 100%;
//       align-items: center;
//       justify-content: center;
//     }
//     .content-main-right-img {
//       width: 100%;
//       height: auto;
//       max-width: 400px;
//     }
//   }

//   .content-secondary {
//     flex-direction: column;
//     justify-content: space-between;
//     width: 100%;
//     margin: 0 auto;
//     .content-secondary-left,
//     .content-secondary-right {
//       width: 100%;
//       display: flex;
//       justify-content: center;
//       align-items: center;
//     }
//     img {
//       width: 100%;
//       height: auto;
//       max-width: 400px;
//       margin: 0;
//     }
//   }

//   .page-weather-loading {
//     padding-top: 80px;
//     top: 50px;
//     .lottle-con {
//       width: 20px;
//       height: 20px;
//     }
//     p {
//       font-size: 16px;
//       margin-top: 0;
//       margin-left: 10px;
//     }
//   }
// }
</style>
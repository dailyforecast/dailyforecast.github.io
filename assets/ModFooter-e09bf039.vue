<script setup lang="ts">
const email = 'dailyforecastapp@outlook.com';
const linkList = [
  {
    isAction: true,
    href: '/terms.html',
  },
  {
    isAction: true,
    href: '/privacy.html',
  }
];

const routeTo = (route: string) => {
  window.open(route);
};
</script>

<template>
  <div class="footer-component">
    <div class="footer-component__header">
      <div class="footer-component__header-top">
        <img class="footer-component__logo" src="@/assets/img/logo.png" />
        <span class="footer-component__name">{{ $t('public') }}</span>
      </div>
      <span class="footer-component__btn android" target="_blank" href="#"
        >google Pay</span
      >
    </div>
    <div class="footer-component__line"></div>
    <div class="footer-component__body">
      <!-- <div class="footer-component__company">{{ $t('footer.comp') }}</div> -->
      <div class="footer-component__call">
        <div class="footer-component__info">
          <template v-for="(item, index) in linkList" :key="index">
            <span class="footer-component__separator" v-if="index > 0"> | </span>
            <span
              class="footer-component__link"
              v-if="linkList[index]['isAction']"
              @click="routeTo(item.href)"
              >{{ $t(`footer.callus[${index}]`) }}</span
            >
           
          </template>
          <span> | </span>
          <a  class="footer-component__link" href="mailto:dailyforecastapp@outlook.com">{{ email }}</a>
        </div>
      </div>

     <!-- <div class="footer-component__company">
        {{ $t('footer.limit') }} | {{ $t('footer.address') }}
      </div> -->

    </div>
  </div>
</template>

<style lang="less">
.footer-component {
  background-color: #ffffff;
  width: 1200px;
  margin: 0 auto;
  padding: 60px 0 60px;

  @media screen and (min-width: 769px) {
    min-width: 1200px;
  }

  .footer-component__header {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .footer-component__header-top {
    display: flex;
    align-items: center;
    margin-right: 40px;
  }

  .footer-component__logo {
    width: 44px;
    height: 44px;
    margin-right: 16px;
  }

  .footer-component__name {
    font-size: 24px;
    font-weight: 600;
    font-family: 'Roboto';
  }

  .footer-component__line {
    width: 100%;
    height: 1px;
    opacity: 0.7;
    background: #999;
    margin: 40px auto;
  }

  .footer-component__body {
    color: #333333;
    line-height: 20px;
    font-size: 16px;
    text-align: center;
  }

  .footer-component__company {
    font-size: 16px;
    &:nth-last-child(1) {
      font-weight: 500;
    }
  }

  .footer-component__call {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 10px auto;

    .footer-component__separator {
      cursor: default;
    }

    .footer-component__link {
      cursor: pointer;
    }

    a.footer-component__link {
      color: #333;
      text-decoration: none;
      transition: all linear 0.2s;
      font-size: 16px;
      &:hover {
        color: #2488ff;
      }
    }
  }

  .footer-component__btn {
    width: 148px;
    height: 44px;
    font-size: 0;
    display: inline-block;
    margin-left: 20px;
    background: no-repeat center;
    background-size: contain;
    opacity: 0.9;
    transition: all linear 0.2s;

    &.android {
      background-image: url('@/assets/img/google_pay.webp');
    }

    &:hover {
      opacity: 1;
    }
  }
}

// @media screen and (max-width: 768px) {
// 	.footer-component {
// 		width: 100%;
// 		padding: 24px 16px;
// 		box-sizing: border-box;
// 		.footer-component__header {
// 			padding-bottom: 10px;
// 		}
// 		.footer-component__header-top {
// 			margin-right: 0;
// 		}
// 		.footer-component__logo {
// 			width: 34px;
// 			height: 34px;
// 			margin-right: 8px;
// 		}
// 		.footer-component__name {
// 			font-size: 18px;
// 			color: #333;
// 		}

// 		.footer-component__line {
// 			margin: 0;
// 			display: none;
// 		}
// 		.footer-component__body {
// 			box-sizing: border-box;
// 			border-top: 1px solid #f5f5f5;
// 			line-height: 16px;
// 			font-size: 14px;
// 		}
// 		.footer-component__company {
// 			margin-top: 8px;
// 			font-size: 14px;
// 			font-weight: normal;
// 			color: #000;
// 			& + .footer-component__company {
// 				margin-top: 0;
// 			}
// 		}
// 		.footer-component__call {
// 			justify-content: center;
// 			flex-direction: row;
// 			flex-wrap: wrap;
// 			margin-top: 10px;
// 			color: #666;
// 			.footer-component__separator {
// 				color: #666;
// 				font-size: 12px;
// 				display: inline-block;
// 				margin: 0 4px;
// 				&:nth-child(4) {
// 					display: none;
// 				}
// 			}
// 			.footer-component__link {
// 				color: #666;
// 				text-decoration: none;
// 				transition: all linear 0.2s;
// 				font-size: 12px;
// 				& ~ .footer-component__separator {
// 					margin-left: 4px;
// 				}
// 				&:hover {
// 					color: #666;
// 				}
// 			}
// 		}
// 		.footer-component__btn {
// 			display: none;
// 		}
// 	}
// }
</style>
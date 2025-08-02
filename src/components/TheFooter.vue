<script setup>
  const topLinksList = [
    'About us',
    'Instructions',
    'Platforms',
    'Contact Us',
    'Sign in',
    'Sign up for free'
  ];
  const bottomLinksList = [
    'Terms and Conditions',
    'Privacy Policy',
    'Risk Warnings',
    'Anti-Money Laundering'
  ];
</script>

<template>
  <footer class="qp__footer">
    <div class="footer__first">
      <div class="footer__logo"><div class="gp__test-logo">Logo</div></div>
      <div class="footer__info">
        <span>Information and high risk warning:</span>
        <p>
          Trading with foreign exchange (FX), contract for differences (CFDs) and precious metals carries a high
          level of risk that may not be suitable for all investors. Leverage creates additional risk and loss exposure.
          Before you decide to trade foreign exchange or contract for differences, carefully consider your investment
          objectives, experience level, and risk tolerance.
        </p>
      </div>
      <div class="footer__info">
        <span>Legal disclaimer:</span>
        <p>Forex trading entails significant risks and is not appropriate for all investors. The possibility of
          incurring substantial losses should be taken into account. It is therefore important to understand the
          possible consequences of investing. Traders should weigh their earning potential against the risks involved
          and act accordingly. Interactive Trade Ltd operating under brand and using domenLink domain within the
          European Economic Area.
        </p>
      </div>
      <ul class="footer__links">
        <li v-for="item of topLinksList" :key="item" class="links-item">
          <a href="#">{{item}}</a>
        </li>
      </ul>
    </div>
    <div class="footer__second">
      <div class="footer__copyr">Copyright 2020, All Right Reserved</div>
      <ul>
        <li v-for="item of bottomLinksList" :key="item">
          <a href="#" >{{item}}</a>
        </li>
      </ul>
    </div>
  </footer>
</template>

<style lang="scss">
@import "../assets/styles/_vars.scss";
.qp__footer {
  padding: 32px 120px 70px;
  background: #ffffff;
  a {
    text-decoration: none;
    color: inherit;
  }
  ul {
    list-style: none;
  }
  .footer {
    &__first {
      display: grid;
      grid-template-columns: 175px 1fr 1fr 175px;
      gap: 30px;
    }
    &__second {
      display: flex;
      margin-top: 48px;
      font-size: 16px;
      line-height: 27px;
      color: #828282;
      .footer__copyr {
        margin-right: 132px;
        min-width: max-content;
      }
      ul {
        display: flex;
        justify-content: space-between;
        width: 100%;
      }
    }
    &__logo {}
    &__info {
      & > span {
        font-family: $font-second;
        font-weight: 500;
        font-size: 18px;
        line-height: 30px;
        color: $text-dark;
      }
      & > p {
        margin-top: 16px;
        font-size: 16px;
        line-height: 27px;
      }
    }
    &__links {
      padding-left: 66px;
      .links-item {
        font-family: $font-second;
        font-weight: 500;
        font-size: 15px;
        line-height: 16px;
        color: $text-dark;
        &:not(:last-child) {
          margin-bottom: 24px;
        }
      }
    }
  }
}
@media screen and (max-width: 1400px) {
  .qp__footer {
    padding: 32px 130px 70px;
    .footer {
      &__first {
        grid-template-columns: 1fr;
        gap: 32px;
      }
      &__second {
        flex-direction: column;
        text-align: center;
        margin-top: 40px;
        ul {
          flex-direction: column;
          margin-top: 16px;
          gap: 16px;
        }
        .footer__copyr {
          margin-right: 0;
        }
      }
      &__logo {
        order: 1;
        height: 64px;
        text-align: center;
      }
      &__links {
        order: 2;
        padding: 4px 0;
        margin: 0 -80px;
        display: flex;
        justify-content: space-between;
        width: calc(100% + 160px);
        .links-item {
          &:not(:last-child) {
            margin-bottom: 0;
          }
        }
      }
      &__info {
        order: 3;
        & > span {
          display: inline-block;
          width: 100%;
          text-align: center;
        }
      }
    }
  }
}
@media screen and (max-width: 600px) {
  .qp__footer {
    padding: 32px 20px 70px;
    .footer {
      &__first {
        gap: 26px;
      }
      &__second {
        margin-top: 32px;
      }
      &__logo {
        height: 36px;
      }
      &__links {
        flex-direction: column;
        width: 100%;
        margin: 0;
        .links-item {
          &:not(:last-child) {
            margin-bottom: 32px;
          }
        }
      }
      &__info {
        & > span {
          text-align: left;
        }
      }
    }
  }
}
</style>

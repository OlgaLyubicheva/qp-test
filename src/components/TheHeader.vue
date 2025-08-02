<script setup>
  const navList = [
    'How it works',
    'About',
    'Instructions',
    'Accounts',
    'Platforms',
    'Contact'];
</script>

<template>
  <header class="qp__header">
    <a href="/" class="header__logo">
      <div class="gp__test-logo">LOGO</div>
    </a>
    <nav class="header__nav">
      <a v-for="item of navList" :key="item" href="#" class="header__link">{{ item }}</a>
    </nav>
    <div style="width: 100%; flex: 1 0"></div>
    <div class="header__tools">
      <button class="qp__btn sm btn-lang">
        en
        <span class="btn-lang__arrow"></span>
      </button>
      <button class="qp__btn prime sm btn-login">Sign in for free</button>
      <button class="btn-menu"></button>
    </div>
  </header>
</template>

<style lang="scss">
@use "../assets/styles/_vars.scss";
.qp__header {
  position: sticky;
  top: 0;
  z-index: 10;
  display: flex;
  align-items: center;
  width: 100%;
  height: 80px;
  padding: 0 60px 0 95px;
  background: #FFFFFF;
  .header {
    &__logo {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 95px;
      height: 64px;
      text-decoration: none;
    }
    &__nav {
      display: flex;
      flex-direction: row;
      align-items: center;
      padding: 0 32px;
      margin-right: auto;
      gap: 32px;
    }
    &__link {
      font-family: vars.$font-second;
      font-style: normal;
      font-weight: 500;
      font-size: 15px;
      line-height: 16px;
      color: #333333;
      text-decoration: none;
      &:hover {
        text-decoration: underline;
      }
    }
    &__tools {
      display: flex;
      align-items: center;
      gap: 24px;
      .btn-lang {
        width: 80px;
        border: 1px solid #000000;
        background: #ffffff;
        &__arrow {
          display: block;
          width: 20px;
          height: 20px;
          background-image: url("../assets/img/qp_arrow_down.svg");
        }
      }
      .btn-login {
        width: 167px;
      }
      .btn-menu {
        display: none;
        width: 24px;
        height: 24px;
        background: url("../assets/img/qp_menu.svg") no-repeat;
      }
    }
  }
}
@media screen and (max-width: 1400px) {
  .qp__header {
    padding: 0 40px;
    .header {
      &__nav {
        display: none;
      }
      &__tools {
        .btn-lang {
          display: none;
        }
        .btn-menu {
          display: block;
          margin-left: 24px;
        }
      }
    }
  }
}
@media screen and (max-width: 600px) {
  .qp__header {
    padding: 0 20px;
    .header {
      &__logo{
        justify-content: left;
      }
      &__tools {
        .btn-login {
          display: none;
        }
      }
    }
  }
}
</style>

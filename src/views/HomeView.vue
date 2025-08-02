<script setup>
  import chartImg from "../assets/img/qp_chart.png";
  import avatarImg from "../assets/img/manager_foto.png";
  import {ref, computed} from "vue";

  const startedList = [
    {id: 1, title: 'Register', text: 'Complete the simple registration to get your trading credentials.'},
    {id: 2, title: 'Verification', text: 'Big Invest is required to verify your identity, upload your documents quickly and get approved in minutes.'},
    {id: 3, title: 'Deposit funds', text: 'Big Invest accepts credit cards and bank wires. Just use the secure deposit form and follow the steps.'},
    {id: 4, title: 'Start Trading', text: 'Once your deposit has been credited, you can begin trading instantly. In no time you will see profits rolling into your account.'},
  ];
  const startedList1 = startedList.filter(item => {
    return item.id%2 !== 0;
  });
  const startedList2 = startedList.filter(item => {
    return item.id%2 === 0;
  });
  const questionsList = [
    {id: 1, title: 'How do I change my details?', text: 'Some text'},
    {id: 2, title: 'What platforms will I be able to use?', text: 'We provide only the best trading software. The trading terminal MetaTrader4 is the most popular and convenient platform for access to global exchanges. You can work anywhere. All you need is the Internet because the necessary trading tools are already collected in one place and are available in a couple of clicks. Use only the best and develop with us!'},
    {id: 3, title: 'How do I change my details?', text: 'Some text'},
    {id: 4, title: 'How do I change my details?', text: 'Some text'},
    {id: 5, title: 'How do I change my details?', text: 'Some text'},
    {id: 6, title: 'How do I change my details?', text: 'Some text'},
    {id: 7, title: 'How do I change my details?', text: 'Some text'},
  ];
  const contactsList = [
    {id: 1, label: "Phone:", data: "442038857261"},
    {id: 2, label: "Email:", data: "help@google.com"},
    {id: 3, label: "Address:", data: "Trust Company Complex, Ajeltake Road, Ajeltake Island, Majuro, Republic of the Marshall Islands, MH 96960"},
  ]

  const testMaxSlides = 4;
  const currentSlideIndex = ref(0);
  function toSlide(add, maxIndex) {
    try {
      const newSlide = currentSlideIndex.value + add;
      if(newSlide > maxIndex) {
        currentSlideIndex.value = maxIndex;
      } else if (newSlide < 0) {
        currentSlideIndex.value = 0;
      } else {
        currentSlideIndex.value = newSlide;
      }
    } catch (error) {
      currentSlideIndex.value = 0;
    }
  }
  function formatPageText(page) {
    return `${page}`.padStart(2, '0');
  }
  const pagesText = computed(() => {
    return formatPageText(currentSlideIndex.value + 1) + ' / ' + formatPageText(testMaxSlides);
  })
</script>

<template>
  <main class="home-v">
    <section class="home-v__top">
      <div>
        <h1 class="top__title">Trade everywhere.<br> Invest here!</h1>
        <p class="top__p">
          We provide only the best trading software. The trading terminal MetaTrader4 is the most popular and
          convenient platform for access to global exchanges. You can work anywhere.
        </p>
        <button class="qp__btn md prime top__btn">Start trading</button>
      </div>
      <div class="top__img">
        <img :src="chartImg" alt="chat">
      </div>
    </section>
    <section class="home-v__info">
      <div class="first-b">
        <h2 class="info-title">
          Getting Started Is Fast & Easy
        </h2>
        <div class="first-b__list">
          <div class="list__all">
            <div v-for="item of startedList" :key="item.id" class="qp__card first-b__card">
              <div class="card__index">{{`${item.id}`.padStart(2, '0')}}.</div>
              <div class="card__title">{{item.title}}</div>
              <div class="card__text">{{item.text}}</div>
            </div>
          </div>
          <div class="list__col">
            <div v-for="item of startedList1" :key="item.id" class="qp__card first-b__card">
              <div class="card__index">{{`${item.id}`.padStart(2, '0')}}.</div>
              <div class="card__title">{{item.title}}</div>
              <div class="card__text">{{item.text}}</div>
            </div>
          </div>
          <div class="list__col">
            <div v-for="item of startedList2" :key="item.id" class="qp__card first-b__card link-before" :class="{'link-after': item.id === 2}">
              <div class="card__index">{{`${item.id}`.padStart(2, '0')}}.</div>
              <div class="card__title">{{item.title}}</div>
              <div class="card__text">{{item.text}}</div>
            </div>
          </div>
        </div>
      </div>
      <div class="second-b">
        <div>
          <h2 class="info-title">
            People love Big Invest
          </h2>
          <div class="second-b__btns-wrapp">
            <button class="second-b__btn left" :disabled="currentSlideIndex === 0" @click="toSlide(-1, testMaxSlides - 1)"></button>
            <button class="second-b__btn right" :disabled="currentSlideIndex === testMaxSlides - 1" @click="toSlide(1, testMaxSlides - 1)"></button>
          </div>
        </div>
        <div class="second-b__slides-wrapp">
          <div v-if="currentSlideIndex === 0" class="second-b__slide">
            <div class="slide__top">
              <div class="slide__img">
                <img :src="avatarImg" alt="avatar">
              </div>
              <div class="slide__person-data">
                <div class="slide__name">Albert Abello</div>
                <div class="slide__position">Director of Growth</div>
              </div>
            </div>
            <p class="slide__p">
              This magical product actually works! It has radically changed the way we build our audiences. Increasing
              new customer sales by 6x in our most mature market.
            </p>
            <div class="slide__pages">{{pagesText}}</div>
          </div>
          <div v-else class="second-b__slide">
            {{currentSlideIndex + 1}}
            <div class="slide__pages">{{pagesText}}</div>
          </div>
          <div class="slides__btns-wrapp">
            <button class="second-b__btn left" :disabled="currentSlideIndex === 0" @click="toSlide(-1, testMaxSlides - 1)"></button>
            <button class="second-b__btn right" :disabled="currentSlideIndex === testMaxSlides - 1" @click="toSlide(1, testMaxSlides - 1)"></button>
          </div>
        </div>
      </div>
      <div class="thirt-b">
        <h2 class="info-title">
          Frequently asked questions
        </h2>
        <div class="accordion">
          <details v-for="item of questionsList" :key="item.id" class="qp__card accordion-item">
            <summary class="accordion-item__header">{{item.title}}</summary>
            <p class="accordion-item__body">{{item.text}}</p>
          </details>
        </div>
      </div>
    </section>
    <section class="home-v__contacts">
      <div class="contacts__info">
        <h2>
          Contact us!
        </h2>
        <p>
          The support staff and customer service are available to help you with any questions or needs you might have.
          Just drop us a line.
        </p>
        <div class="contacts__contacts">
          <p>This site is owned and operated by Kode Tech Solutions LTD</p>
          <div v-for="item of contactsList" :key="item.id" class="contacts__item">
            <span>{{item.label}}</span><br>
            {{item.data}}
          </div>
        </div>

      </div>
      <div class="contacts__form-wrapp qp__card">
        <form>
          <input type="text" placeholder="Name" name="name" class="qp__input form__field">
          <input type="text" placeholder="Email" name="email" class="qp__input form__field">
          <textarea placeholder="Message" name="message" class="qp__input form__field"/>
          <button type="submit" class="qp__btn md prime form__btn" @click.prevent="() => {}">Send</button>
        </form>
      </div>
    </section>
  </main>
</template>

<style lang="scss">
@import "../assets/styles/_vars.scss";
.home-v {
  &__top {
    display: flex;
    justify-content: space-between;
    min-height: 720px;
    padding: 100px 120px 98px; //100px 120px;
    gap: 120px;
    background: $bg-light-prime;
    .top {
      &__title {
        font-family: $font-second;
        font-weight: bold; //500;
        font-size: 64px;
        line-height: 72px;
        color: $text-dark;
        margin: 40px 0 30px; //32px;
      }
      &__p {
        width: 483px;
        font-size: 18px;
        line-height: 30px;
      }
      &__btn {
        margin-top: 48px;
        width: 257px;
      }
      &__img {
        img {
          width: inherit;
        }
      }
    }
  }
  &__info {
    display: flex;
    flex-direction: column;
    padding: 140px 120px;
    gap: 140px;
    .info-title {
      position: relative;
      max-width: 483px;
      font-family: $font-second;
      color: $text-dark;
      font-weight: 500;
      font-size: 56px;
      line-height: 66px;

      &::after {
        content: "";
        position: absolute;
        left: 0;
        bottom: 0;
        width: 60%;
        height: 50%;
        background: $bg-light-prime;
      }
    }
    .first-b {
      &__list {
        display: flex;
        justify-content: space-between;
        gap: 134px 30px;
        max-width: 1098px;
        min-height: 750px;
        margin-top: 60px;
        .list__col {
          display: flex;
          flex-direction: column;
          gap: 134px;
          &:not(:last-child) {
            .first-b__card {
              z-index: 2;
            }
          }
          &:last-child {
            padding-top: calc(134px + 1%);
          }
        }
        .list__all {
          display: none;
        }
      }
      &__card {
        position: relative;
        max-width: 483px;
        border-radius: 30px;
        z-index: 1;

        &.link-before {
          &::before {
            content: "";
            position: absolute;
            z-index: 0;
            top: -26%;
            left: -50%;
            width: 100%;
            height: 25%;
            border-radius: 0 30px 0 0;
            border: dashed $prime-color;
            border-width: 3px 3px 0 0;
          }
        }
        &.link-after {
          &::after {
            content: "";
            position: absolute;
            z-index: 0;
            top: 50%;
            right: 100%;
            width: 80%;
            height: 50%;
            border-radius: 30px 0 0 0;
            border: dashed $prime-color;
            border-width: 3px 0 0 3px;
          }
        }

        /*&:nth-child(2n) {
          justify-self: right;
          transform: translateY(calc(50% + 67px));
        }*/
        .card {
          &__index {
            font-family: $font-second;
            font-weight: 500;
            font-size: 15px;
            line-height: 18px;
            color: $prime-color;
          }
          &__title {
            font-family: $font-second;
            font-weight: 500;
            font-size: 24px;
            line-height: 29px;
            color: $text-dark;
            margin: 8px 0 24px;
          }
          &__text {
            font-size: 18px;
            line-height: 30px;
            //color: #4F4F4F;
          }
        }
      }
    }
    .second-b {
      position: relative;
      display: flex;
      justify-content: space-between;
      max-width: 1200px;
      //margin: 0 auto;
      &__btns-wrapp {
        display: flex;
        gap: 16px;
        margin-top: 47px;
      }
      &__btn {
        width: 48px;
        height: 48px;
        border-radius: 50%;
        border: 1px solid $prime-color;
        background: #ffffff no-repeat center center;

        &:disabled {
          border-color: #E0E0E0;
          pointer-events: none;
        }
        &.left {
          background-image: url("../assets/img/qp_arrow_l.svg");
        }
        &.right {
          background-image: url("../assets/img/qp_arrow_r.svg");
        }
      }
      &__slides-wrapp {
        max-width: 633px;
        padding-top: 27px;
        overflow: hidden;
        .slides__btns-wrapp {
          display: none;
        }

      }
      &__slide {
        position: relative;
        display: flex;
        flex-direction: column;
        padding-left: 48px;
        height: 100%;
        min-height: 256px;
        min-width: 600px;
        &::before {
          content: "";
          position: absolute;
          top: 90px;
          left: 0;
          width: 33px;
          height: 33px;
          background: url("../assets/img/qp_quote.svg") no-repeat;
          background-size: contain;
        }
        .slide__top {
          display: flex;
        }
        .slide__img {
          width: 73px;
          height: 73px;
          border-radius: 50%;
          margin-right: 30px;
          & > img {
            width: inherit;
            border-radius: inherit;
            object-fit: contain;
          }
        }
        .slide__person-data {
          display: flex;
          flex-direction: column;
          justify-content: center;
        }
        .slide__name {
          font-family: $font-second;
          font-weight: 500;
          font-size: 18px;
          line-height: 30px;
          color: $text-dark;
        }
        .slide__position {
          font-size: 16px;
          line-height: 27px;
        }
        .slide__p {
          margin: 17px 0 31px;
          font-family: $font-second;
          font-weight: 500;
          font-size: 24px;
          line-height: 29px;
          color: $text-dark;
        }
        .slide__pages {
          font-family: $font-second;
          font-weight: 500;
          font-size: 15px;
          line-height: 18px;
          color: $prime-color;
          margin-top: auto;
        }
      }
    }
    .thirt-b {
      .accordion {
        display: flex;
        flex-direction: column;
        max-width: 995px;
        margin: 68px auto 0;
        gap: 16px;
      }
      .accordion-item {
        transition: all 0.3s ease;
        padding: 32px 40px;
        &[open] > .accordion-item__header::after {
          background: url("../assets/img/qp_cross.svg") no-repeat;
        }
        &__header {
          position: relative;
          font-family: $font-second;
          font-weight: 500;
          font-size: 24px;
          line-height: 29px;
          color: $text-dark;

          &::marker {
            content: "";
          }
          &::after {
            content: "";
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            right: -2px;
            width: 32px;
            height: 32px;
            background-size: contain;
            background: url("../assets/img/qp_plus.svg") no-repeat center center;
          }

        }
        &__body {
          padding: 24px 120px 0 0;
          font-size: 16px;
          line-height: 27px;
        }
      }
    }
  }
  &__contacts {
    display: flex;
    align-items: center;
    gap: 120px;
    min-height: 739px;
    padding: 120px;
    background: $bg-light-prime;
    .contacts {
      &__info {
        & > h2 {
          font-family: $font-second;
          font-weight: 500;
          font-size: 56px;
          line-height: 66px;
          color: $text-dark;
        }
        & > p {
          margin: 32px 0 48px;
          font-size: 18px;
          line-height: 30px;
        }
      }
      &__contacts {
        font-size: 16px;
        line-height: 27px;
        & > p {
          margin-bottom: 24px;
        }
      }
      &__item {
        &:not(:last-child) {
          margin-bottom: 16px;
        }
        & > span {
          font-family: $font-second;
          font-weight: 500;
          font-size: 15px;
          line-height: 16px;
          color: $text-dark;
        }
      }
      &__form-wrapp {
        min-width: 585px;
        //height: 471px;
        padding: 80px;
        .form {
          &__btn {
            width: 172px;
            margin: 40px auto 0;
          }
          &__field {
            width: 100%;
            margin-bottom: 24px;
          }
        }
        textarea.form__field {
          height: 89px;
          resize: none;
          margin-bottom: 0;
        }
      }
    }
  }
}
@media screen and (max-width: 1400px) {
  .home-v {
    &__top {
      flex-direction: column;
      //justify-content: center;
      align-items: center;
      gap: 32px;
      padding: 40px 100px 26px;
      & :first-child {
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
      }
      .top {
        &__title {
          margin: 0 0 30px;
        }
        &__img {
          width: 418px;
        }
        &__p {
          width: 500px;
        }
      }
    }
    &__info {
      padding: 120px 40px;
      gap: 120px;
      .second-b {
        flex-direction: column;
        &__btns-wrapp {
          display: none;
        }
        &__slides-wrapp {
          position: relative;
          max-width: 100%;
          padding: 0 80px;
          margin-top: 56px;
          .slides__btns-wrapp {
            position: absolute;
            //bottom: 50%;
            //transform: translateY(-50%);
            top: 158px;
            left: 0;
            right: 0;
            margin: 0;
            display: flex;
            width: 100%;
            justify-content: space-between;
          }
        }
        &__slide {
          text-align: center;
          padding-left: 0;
          min-height: 336px;
          min-width: auto;
          &::before {
            top: 158px;
            left: 50%;
            transform: translateX(-50%);
          }
          .slide__top {
            width: 100%;
            flex-direction: column;
            align-items: center;
            justify-content: center;
          }
          .slide__img {
            margin: 0 0 10px 0;
          }
          .slide__p {
            margin-top: 59px;
          }
        }
      }
      .thirt-b {
        .accordion {
          margin: 56px auto 0;
          .accordion-item {
            &__body {
              padding: 24px 40px 0 0;
            }
            &__header {
              &::after {
                right: -26px;
              }
            }
          }
        }
      }
    }
    &__contacts {
      flex-direction: column;
      padding: 48px 130px;
      gap: 48px;
      .contacts {
        &__info {
          & > h2 {
            text-align: center;
          }
          & > p {
            margin: 32px 0;
          }
        }
        &__contacts {
          & > p {
            margin-bottom: 20px;
          }
        }
        &__item {
          &:not(:last-child) {
            margin-bottom: 16px;
          }
        }
        &__form-wrapp {
          min-width: auto;
          max-width: 508px;
          padding: 80px 42px;
        }
      }
    }
  }
}
@media screen and (max-width: 600px) {
  .home-v {
    &__top {
      padding: 33px 20px 20px;
      & :first-child {
        align-items: start;
        text-align: left;
      }
      .top {
        &__title {
          font-size: 40px;
          line-height: 44px;
          margin: 0 0 24px;
        }
        &__p {
          width: auto;
        }
        &__img {
          width: 240px;
          padding: 20px 0;
        }
        &__btn {
          margin-top: 30px;
        }
      }
    }
    &__info {
      padding: 80px 20px;
      gap: 80px;
      .first-b {
        &__list {
          margin-top: 40px;
          .list__col {display: none}
          .list__all {
            display: flex;
            flex-direction: column;
            gap: 24px;
          }
        }
        &__card {
          padding: 24px;
          .card {

          }
        }
      }
      .second-b {
        &__slides-wrapp {
          padding: 0 0 15px 0;
          margin-top: 38px;
          .slides__btns-wrapp {
            bottom: 0;
            top: unset;
            transform: translateY(0);
          }
        }
        &__slide {
          min-height: 418px;
          &::before {
            top: 162px;
          }
          .slide__p {
            margin: 74px 0 40px;
          }

        }
      }
      .info-title {
        font-size: 40px;
        line-height: 44px;
        max-width: 250px;
        &::after {
          height: 44px;
          width: 84%;
        }
      }
      .thirt-b {
        .accordion {
          margin: 38px auto 0;
          .accordion-item {
            border-radius: 15px;
            padding: 24px 70px 22px 16px;
            &__header {
              font-size: 18px;
              line-height: 21px;
              &::after {
                right: -56px;
              }
            }
            &__body {
              padding: 24px 0 0 0;
              margin-right: -50px;
              font-size: 16px;
              line-height: 27px;
            }
          }
        }
      }
    }
    &__contacts {
      padding: 50px 20px;
      .contacts {
        &__info {
          & > h2 {
            font-size: 40px;
            line-height: 44px;
            text-align: start;
          }
          & > p {
            margin: 24px 0;
          }
        }
        &__contacts {
          & > p {
            margin-bottom: 10px;
          }
        }
        &__form-wrapp {
          padding: 48px 16px;
        }
      }
    }
  }
}
</style>

<template>
  <div class="head">
    <div class="head__img">
      <div class="head__img__block"></div>
    </div>
  </div>
  <main class="main">
    <div class="container">
      <div class="main__inner">
        <h1 class="main__title">Giorni, luoghi e orari</h1>
      </div>
    </div>
    <div class="hr"></div>
    <div class="container">
      <h3 class="main__subtitle">Quando si svolge il servizio</h3>
    </div>
    <div class="tabs" v-on:click="changeClass">
      <button class="tabs__item active">Giorni</button>
      <button class="tabs__item">In data</button>
    </div>

    <div class="days">
      <div class="container">
        <div v-on:click="toggleClass" class="days__inner">
          <div class="days__item">Lu</div>
          <div class="days__item">Ma</div>
          <div class="days__item">Me</div>
          <div class="days__item">Gi</div>
          <div class="days__item">Ve</div>
          <div class="days__item">Sa</div>
          <div class="days__item">Do</div>
        </div>
        <h3 class="main__subtitle days__subtitle">
          Orario di partenza da Cervinia o incontro
        </h3>
        <div class="days__hour">
          <div class="days__hour__from">
            <select class="days__hour__select">
              <option class="days__hour__select__option"> 14:00</option>
              <option class="days__hour__select__option"> 15:00</option>
              <option class="days__hour__select__option"> 16:00</option>
              <option class="days__hour__select__option"> 17:00</option>
            </select>
          </div>
          <div class="days__hour__by">
            <select class="days__hour__select">
              <option class="days__hour__select__option"> 18:00</option>
              <option class="days__hour__select__option"> 19:00</option>
              <option class="days__hour__select__option"> 20:00</option>
              <option class="days__hour__select__option"> 21:00</option>
            </select>
          </div>
        </div>
        <h3 class="main__subtitle">
          Luogo di partenza o incontro con i clienti
        </h3>
        <div class="main__map">
          <iframe
            src="https://www.google.com/maps/embed?pb=!1m10!1m8!1m3!1d609.4784850211981!2d12.114999670776868!3d43.194948541419365!3m2!1i1024!2i768!4f13.1!5e1!3m2!1sru!2sua!4v1614807821662!5m2!1sru!2sua"
            style="border:0;"
            allowfullscreen=""
            loading="lazy"
          ></iframe>
        </div>

        <div class="main__button">
          <button class="main__button__item">
            <span class="main__button__item__span">+</span> Aggiungi
          </button>
        </div>
        <div class="main__done">
          <button class="main__done__item">Done</button>
        </div>
        <div class="main__indicator">
          <div class="main__indicator__item"></div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "Popup",
  methods: {
    toggleClass: function(e) {
      e.target.classList.toggle("active");
    },
    changeClass: function(e) {
      if (e.target) {
        e.target.parentNode.childNodes.forEach((item) => {
          item.classList.remove("active");
        });
        e.target.classList.add("active");
      }
    },
  },
};
</script>

<style>
*,
*:before,
*:after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.container {
  max-width: 345px;
  width: 100%;
  margin: auto;
}

.head__img {
  width: 100%;
  background-color: #979797;
  position: relative;
  height: 150px;
}

.head__img__block {
  position: absolute;
  border-radius: 3px;
  background-color: #fff;
  width: 70px;
  height: 5px;
  left: 50%;
  top: 73%;
  transform: translateX(-50%);
}

.main {
  background-color: #fff;
  box-shadow: 0px 4px 4px rgba(218, 218, 218, 0.2);
  margin-top: -30px;
  border-radius: 15px 15px 0px 0px;
  position: relative;
  z-index: 10;
}

.main__title {
  padding: 20px 0;
  font-family: Arial;
  font-weight: 400;
  font-size: 16px;
  line-height: 1.2;
  color: #2d2c31;
  text-align: center;
}
.hr {
  width: 100%;
  height: 2px;
  color: #f5f5f5;
  background-color: #f5f5f5;
  margin-bottom: 30px;
}

.main__subtitle {
  font-family: Arial;
  font-weight: 400;
  font-size: 16px;
  line-height: 1.2;
  color: #2d2c31;
  margin-bottom: 20px;
}

.tabs {
  width: 100%;
  display: flex;
  margin-bottom: 30px;
}

.tabs__item {
  width: 50%;
  font-weight: 700;
  font-size: 16px;
  line-height: 18px;
  padding: 17px 0;
  border-radius: 10px 10px 0px 0px;
  color: #979797;
  background: #f5f5f5;
  outline: none;
  border: none;
  border-bottom: 1px solid #ccc;
}
.tabs__item.active {
  border: 1px solid #ccc;
  border-bottom: none;
  color: #016dc4;
  background-color: #fff;
}

.days__inner {
  display: flex;
  margin: 0 -3px;
  background-color: #fff;
  margin-bottom: 30px;
}
.days__item {
  display: flex;
  justify-content: center;
  align-items: center;
  flex: 1;
  width: 44px;
  height: 44px;
  background: #f5f5f5;
  border-radius: 4px;
  margin: 0 3px;
  transition: 0.2s linear all;

  font-family: Arial;
  font-weight: 700;
  font-size: 16px;
  line-height: 1.2;
  color: #979797;
  cursor: pointer;
}

.days__item.active {
  transition: 0.2s linear all;
  background: #0b86d8;
  box-shadow: 0px 4px 10px rgba(6, 37, 83, 0.15);
  color: #fff;
}

.days__subtitle {
  margin-bottom: 10px;
}

.days__hour {
  width: 100%;
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}
.days__hour__from,
.days__hour__by {
  position: relative;
  flex: 1;
  margin-right: 10px;
}
.days__hour__by {
  margin-right: 0;
}
.days__hour__select {
  text-align: center;
  font-size: 20px;
  line-height: 18px;
  color: #2d2c31;
  width: 100%;
  -webkit-appearance: none;
  -moz-appearance: none;
  -ms-appearance: none;
  appearance: none;
  background: url("../assets/down-chevron.svg") no-repeat center;
  background-position-x: 90%;
  background-size: 8px;

  background-color: #ffffff;
  border: 0.5px solid #efeeec;
  box-shadow: 0px 4px 4px rgba(218, 218, 218, 0.2);
  border-radius: 4px;
  padding: 20px 20px 20px 70px;
  outline: none;
  position: relative;
}
.days__hour__from:after,
.days__hour__by:after {
  z-index: 1;
  padding-left: 95px;
  content: "dalle";
  position: absolute;
  top: 40%;
  left: 0;
  transform: translateX(-50%);
  color: #979797;
  font-size: 14px;
  line-height: 1.2;
}
.days__hour__by:after {
  content: "alle";
}

.days__hour__select__option {
  color: #2d2c31;
}
.main__map {
  max-width: 100%;
  height: auto;
  margin-bottom: 20px;
}
.main__map iframe {
  width: 100%;
  height: 95px;
}
.main__button {
  width: 100%;
  display: flex;
  justify-content: flex-end;
  margin-bottom: 32px;
}
.main__button__item {
  padding: 12px 20px;
  background: #016dc4;
  border-radius: 4px;
  color: #fff;
  border: none;
  outline: none;
  font-weight: 700;
  font-size: 16px;
  line-height: 1.2;
}
.main__button__item__span {
  margin-right: 7px;
}
.main__done {
  margin-bottom: 10px;
}
.main__done__item {
  width: 100%;
  background: #016dc4;
  border-radius: 4px;
  padding: 17px 0;
  font-weight: 700;
  font-size: 16px;
  line-height: 1.2;
  color: #ffffff;
  border: none;
  outline: none;
}
.main__indicator {
  padding: 8px 0;
}
.main__indicator__item {
  width: 135px;
  height: 5px;
  margin: 0 auto;
  background: #000000;
  border-radius: 2.5px;
}
</style>

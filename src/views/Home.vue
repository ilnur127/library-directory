<template>
  <div class="home">
    <Loader v-if="loading" />
    <div
      v-else
    >
      <div class="card__title">
        <div style="display:flex;flex-direction: column;margin-right: 5px;">
            <img src="../assets/Ellipse2.png" style="width: 10px;height: 10px;" alt="">
            <img src="../assets/Ellipse1.png" style="width: 10px;height: 10px;" alt="">
            <img src="../assets/Ellipse2.png" style="width: 10px;height: 10px;" alt="">
        </div>
        {{ title }}
      </div>
      <ul
        class="list"
        v-for="lib of categories"
        :key="lib._id"
      >
        <li
            class="list-item"
            @click="$router.push('/detail/' + lib._id)"
        >
            <span class="list-item__title">{{lib.nativeName}}</span>
            <span class="list-item__hoverText">
                Узнать больше
                <span style="display: flex;width: 50px;justify-content: space-around;">
                    <img src="../assets/Ellipse1.png" style="width: 10px;height: 10px;" alt="">
                    <img src="../assets/Ellipse2.png" style="width: 10px;height: 10px;" alt="">
                    <img src="../assets/Ellipse3.png" style="width: 10px;height: 10px;" alt="">
                </span>
            </span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Loader from '../components/Loader.vue'
export default {
  name: 'Home',
  components: {
    Loader
  },
  data: () => ({
    loading: true,
    title: 'Список библиотек',
    categories: [],
    hover: false
  }),
  async mounted () {
    const categories = await require('../data-52-structure-3.json')
    for (const o in categories) {
      this.categories.push(categories[o])
    }
    console.log(this.categories)
    this.loading = false
  }
}
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap');

* {
    box-sizing: border-box;
}

body {
    font-family: Inter, Roboto, Oxygen, Fira Sans, Helvetica Neue, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-size: 16px;
    background: #cccccc;
    padding: 0;
    margin: 0;
}

.card {

}

.card__title {
    text-align: left;
    margin-left: 50px;
    color: #7C7C7C;
    font-family: Roboto, sans-serif;
    font-style: normal;
    font-weight: normal;
    font-size: 30px;
    line-height: 35px;
    display: flex;
    align-items: center;
}

.list {
    padding: 0;
    list-style: none;
    height: 70px;
    background: #fff;
    margin: 10px 0px;
}

hr {
    margin: 1rem 0;
}

strong,
.bold {
    font-weight: bold;
}

ol,
p,
ul {
    line-height: 1.7;
}

a {
    color: #3eaf7c;
    font-weight: 500;
    text-decoration: none;
}

h1,
h2,
h3,
h4,
h5,
h6 {
    font-weight: 500;
    line-height: 1.45;
}

h1 {
    font-size: 2.2rem;
    font-weight: 600;
}

h2 {
    font-size: 1.65rem;
    padding-bottom: 0.3rem;
    border-bottom: 1px solid #eaecef;
}

h3 {
    font-size: 1.35rem;
}

.primary {
   color: #42b983;
}

.danger {
   color: #e53935;
}

.btn {
    color: #42b983;
    position: relative;
    place-content: center;
    place-items: center;
    width: fit-content;
    border-radius: 99px;
    letter-spacing: 0.05em;
    border: 1px solid #42b983;
    text-decoration: none;
    text-transform: uppercase;
    margin-right: 10px;
    padding: 0.5rem 1.5rem;
    white-space: nowrap;
    font-weight: 700;
    outline: none;
    background: #fff;
    transition: all 0.22s;
}

.btn:hover {
    cursor: pointer;
    background: #42b983;
    color: #fff;;
}

.btn:disabled {
    cursor: not-allowed;
    opacity: 1!important;
    background: #eee!important;
    border-color: #ddd!important;
    color: #999!important;
}

.btn:active {
    box-shadow: inset 1px 1px 1px rgba(0, 0, 0, 0.3);
}

.container {
    margin: 0 auto;
    max-width: 1000px;
}

.container.with-nav {
    margin-top: 70px;
}

.pt-2 {
    padding-top: 2rem;
}

.pt-1 {
    padding-top: 1rem;
}

.pt-5 {
    padding-top: 5rem;
}

.form-control {
    position: relative;
    margin-bottom: 0.5rem;
}

.form-control input,
.form-control select {
    margin: 0;
    outline: none;
    border: 2px solid #ccc;
    display: block;
    width: 100%;
    color: #2c3e50;
    padding: 0.5rem 1.5rem;
    border-radius: 3px;
    font-size: 1rem;
}

.form-control small {
    color: #e53935;
}

.form-control.invalid input {
    border-color: #e53935;
}

.form-checkbox {
    margin-bottom: 1rem;
}

.form-checkbox .label {
    display: block;
    margin: 0 0 0.3rem 0.3rem;
    font-weight: 500;
}

.form-checkbox .checkbox input {
    margin-right: 1rem;
}

.form-control label {
    display: block;
    margin: 0 0 0.3rem 0.3rem;
    font-weight: 500;
}

.form-control input:active,
.form-control input:focus {
    transition: border 0.22s;
    border: 2px solid #42b983;
}

.card {
    overflow: hidden;
    padding: 1rem;
    margin-bottom: 1rem;
    border-radius: 10px;
    box-shadow: 2px 3px 10px rgba(0, 0, 0, 0.2);
    background: #fff;
}

.card.marked {
    border: 4px solid #42b983;
}

.card.center {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.list-item {
    display: flex;
    transition: .22s all;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
    cursor: pointer;
    height: 100%;
}

.list-item__title {
    display: flex;
    align-items: center;
    height: 100%;
    width: 96%;
    background: #C1C1C1;
    border-top-right-radius: 50px;
    border-bottom-right-radius: 50px;
    font-family: Roboto;
    font-style: normal;
    font-weight: normal;
    font-size: 30px;
    line-height: 47px;
    padding-left: 46px;
    color: #fff;
    transition: .22s all;
}

.list-item__hoverText {
    display: none;
    color: #7C7C7C;
    transition: .22s all;
}

.list-item:hover .list-item__title{
    width: 50%;
    background: #C7884A;
}
.list-item:hover .list-item__hoverText{
    display: flex;
    align-items: center;
    justify-content: space-evenly;
    align-self: center;
    margin: 0px 15%;
    width: 200px;
}
.list-item:hover{
    background: #eeefee;
    height: 80px;
}
.alert {
    padding: 1rem 1.5rem;
    border-left-width: .5rem;
    border-left-style: solid;
    margin: 1rem 0;
    position: relative;
    border-bottom-right-radius: 2px;
    border-top-right-radius: 2px;
}

.alert.primary {
    border-color: #42b983;
    background-color: #f8f8f8;
}

.alert.danger {
    border-color: #e53935;
    background-color: #f8f8f8;
}

.alert.warning {
    border-color: #c25205;
    background-color: #f8f8f8;
}

.alert p {
    color: #222;
    line-height: 1.7;
}

.alert-title {
    text-transform: uppercase;
    font-weight: 600;
    margin-bottom: -.4rem;
    color: #222;
}

.modal {
    position: fixed;
    top: 60px;
    width: 600px;
    padding: 1rem;
    background: #fff;
    z-index: 1000;
    left: 50%;
    border-radius: 10px;
    transform: translateX(-50%);
    box-shadow: 2px 3px 10px rgba(0, 0, 0, 0.2);
}

.modal-backdrop {
    position: fixed;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    background: rgba(0, 0, 0, .35);
}

.loader {
    font-size: 10px;
    margin: 50px auto;
    text-indent: -9999em;
    width: 11em;
    height: 11em;
    border-radius: 50%;
    background: #ffffff;
    background: -moz-linear-gradient(left, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    background: -webkit-linear-gradient(left, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    background: -o-linear-gradient(left, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    background: -ms-linear-gradient(left, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    background: linear-gradient(to right, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    position: relative;
    -webkit-animation: load3 1.4s infinite linear;
    animation: load3 1.4s infinite linear;
    -webkit-transform: translateZ(0);
    -ms-transform: translateZ(0);
    transform: translateZ(0);
}
.loader:before {
    width: 50%;
    height: 50%;
    background: #ffffff;
    border-radius: 100% 0 0 0;
    position: absolute;
    top: 0;
    left: 0;
    content: '';
}
.loader:after {
    background: #2c3e50;
    width: 75%;
    height: 75%;
    border-radius: 50%;
    content: '';
    margin: auto;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
}
@-webkit-keyframes load3 {
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(360deg);
        transform: rotate(360deg);
    }
}
@keyframes load3 {
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }
    100% {
        -webkit-transform: rotate(360deg);
        transform: rotate(360deg);
    }
}

.navbar {
    display: flex;
    padding: 0 2rem;
    justify-content: space-between;
    align-items: center;
    position: fixed;
    z-index: 20;
    top: 0;
    left: 0;
    right: 0;
    height: 56px;
    background-color: #fff;
    box-sizing: border-box;
    border-bottom: 1px solid #eaecef;
}

.navbar-menu {
    list-style: none;
    display: flex;
}

.navbar-menu li {
    margin-right: 2rem;
}

.navbar-menu li a {
    color: #2c3e50;
    text-decoration: none;
}

.navbar-menu li a:hover, .navbar-menu li a.active {
    border-bottom: 2px solid #3eaf7c;
}
</style>

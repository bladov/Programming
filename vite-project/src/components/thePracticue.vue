<template>
  <div class="wrapper">
    <div class="left-column">
      <h3 class="title">Практические модули</h3>
      <p class="text">
        Работа над собственными проектами: практика групповых взаимодействий,
        кейс-методы, эссе
      </p>
    </div>
    <div class="right-column">
      <h3 class="title">Итоговая аттестация</h3>
      <ul class="list">
        <li class="item">
          Бизнес-проектирование (подготовка итоговой аттестационной работы,
          консультирование по бизнес-проектированию)
        </li>
        <li class="item">Защита итоговой аттестационной работы</li>
      </ul>
    </div>
  </div>
</template>
<script setup></script>
<style scoped lang="scss">
.wrapper {
  display: flex;
  column-gap: 30px;
  padding-bottom: 80px;
  padding-top: 145px;

  @media (max-width: 900px) {
    flex-direction: column;
    padding-top: 45px;
    padding-bottom: 40px;
    row-gap: 20px;
  }
}
.left-column {
  padding: 56px 60px 92px 72px;
  position: relative;
  background: #ff3535;

  @media (max-width: 600px) {
    padding: 31px 17px;
  }
}
.left-column::after {
  content: "";
  position: absolute;
  right: 0;
  top: 0;
  border: 20px solid transparent;
  border-bottom: 20px solid #cd1800;
  border-left: 20px solid #cd1800;
}

.left-column::before {
  content: "";
  position: absolute;
  right: 0;
  top: 0;
  border: 20px solid transparent;
  border-top: 20px solid #ffffff;
  border-right: 20px solid #ffffff;
}
.title {
  margin-bottom: 25px;
  font-weight: 700;
  font-size: 36px;
  line-height: 120%;
  color: #ffffff;

  @media (max-width: 600px) {
    font-size: 25px;
  }
}
.text {
  font-weight: 300;
  font-size: 20px;
  line-height: 130%;
  color: #ffffff;
}
.right-column {
  padding: 52px 53px 55px 57px;
  background: #2d2c2a;

  @media (max-width: 600px) {
    padding: 31px 17px;
  }
}
.list {
  padding-left: 10px;
}
.item {
  font-weight: 300;
  font-size: 20px;
  line-height: 130%;
  color: #ffffff;
}

.item:not(:last-child) {
  margin-bottom: 10px;
}

ul {
  list-style: disc;
}

ul li::marker {
  color: #ff3535;
  font-size: 1em;
}
</style>

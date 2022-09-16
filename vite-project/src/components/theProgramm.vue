<template>
  <section>
    <p v-if="!this.programm" class="loader">загружаю...</p>
    <template v-if="this.programm">
      <template v-for="n in 5">
        <h2 class="title">{{ this.programm[n - 1].title }}</h2>
        <div class="wrapper">
          <div class="module">
            <h3
              class="subtitle"
              @click="toggleActive(n)"
              :class="{ 'subtitle--active': accordion[n - 1].isActive }"
            >
              1 модуль
            </h3>
            <div class="list-wrapper">
              <ul class="list" :class="{ active: accordion[n - 1].isActive }">
                <li class="item" v-for="b in listLengthFirst(getLenght(n - 1))">
                  {{ this.programm[n - 1].specializedSubjects[b - 1].string }}
                </li>
              </ul>
            </div>
          </div>

          <div class="module">
            <h3
              class="subtitle"
              :class="{ 'subtitle--active': accordionSecond[n - 1].isActive }"
              @click="toggleActiveSecond(n)"
            >
              2 модуль
            </h3>
            <div class="list-wrapper">
              <ul
                class="list"
                :class="{ active: accordionSecond[n - 1].isActive }"
              >
                <li
                  class="item"
                  v-for="b in listLengthSecond(getLenght(n - 1))"
                >
                  {{ this.programm[n - 1].specializedSubjects[b - 1].string }}
                </li>
              </ul>
            </div>
          </div>
        </div>
      </template>
    </template>
  </section>
</template>

<script>
export default {
  name: "theProgramm",

  data() {
    return {
      programm: null,

      accordion: [
        { id: 1, isActive: false },
        { id: 2, isActive: false },
        { id: 3, isActive: false },
        { id: 4, isActive: false },
        { id: 5, isActive: false },
      ],

      accordionSecond: [
        { id: 1, isActive: false },
        { id: 2, isActive: false },
        { id: 3, isActive: false },
        { id: 4, isActive: false },
        { id: 5, isActive: false },
      ],
    };
  },

  methods: {
    listLengthFirst(num) {
      if (num % 2 !== 0) {
        return Math.round(num / 2);
      }

      return num / 2;
    },
    listLengthSecond(num) {
      if (num % 2 !== 0) {
        return Math.floor(num / 2);
      }

      return num / 2;
    },

    getLenght(index) {
      return this.programm[index].specializedSubjects.length;
    },

    toggleActive(n) {
      const width = document.body.getBoundingClientRect().width;
      if (width > 584) return;
      this.accordion[n - 1].isActive = !this.accordion[n - 1].isActive;
    },

    toggleActiveSecond(n) {
      const width = document.body.getBoundingClientRect().width;
      if (width > 584) return;

      this.accordionSecond[n - 1].isActive =
        !this.accordionSecond[n - 1].isActive;
    },
  },

  async created() {
    console.log("before");
    const response = await fetch(
      "https://api-moscow-mba.herokuapp.com/products"
    );
    const json = await response.json();
    this.programm = json;

    console.log("after");
    console.log(this.programm[0].specializedSubjects);
    console.log(this.programm[0]);
  },
};
</script>
<style scoped lang="scss">
.loader {
  background-color: gray;
  text-align: center;
  padding: 20px;
  font-size: 26px;
  line-height: 120%;
}
.title {
  margin-bottom: 55px;
  font-weight: 700;
  font-size: 26px;
  line-height: 120%;

  @media (max-width: 600px) {
    padding-top: 35px;
    margin-bottom: 27px;
  }
}
.wrapper {
  display: flex;
  column-gap: 2.5rem;

  @media (max-width: 600px) {
    z-index: 6;
    flex-direction: column;
  }
}
.module {
  display: flex;
  column-gap: 4rem;

  @media (max-width: 900px) {
    flex-direction: column;
  }
}

.module:not(:last-child) {
  margin-bottom: 80px;

  @media (max-width: 600px) {
    margin-bottom: 10px;
  }
}
.subtitle {
  position: relative;
  min-width: 160px;
  padding-top: 30px;
  border-top: 2px solid #ff3535;
  font-size: 32px;
  line-height: 120%;
  transition: all 0.3s ease-in-out;

  @media (max-width: 600px) {
    padding: 15px 10px 15px 70px;
    font-weight: 300;
    font-size: 18px;
    line-height: 130%;
    color: #262626;
    border: none;
    background: #f7f7f7;

    &:hover {
      background: gray;
    }
  }

  &::before {
    position: absolute;
    display: none;
    content: "";
    top: 50%;
    left: 20px;
    border: 2px solid #d9d9d9;
    width: 18px;

    @media (max-width: 600px) {
      display: block;
    }
  }

  &::after {
    position: absolute;
    display: none;
    content: "";
    top: 50%;
    left: 20px;
    border: 2px solid #d9d9d9;
    width: 18px;
    transform: rotate(90deg);

    @media (max-width: 600px) {
      display: block;
    }
  }
}

.subtitle--active {
  background-color: #ff3535;
  color: #ffffff;

  &::after {
    display: none;
  }

  &:hover {
    background: #ff3535;
  }
}

.list-wrapper {
  @media (max-width: 600px) {
    position: relative;
    overflow: hidden;
  }
}
.list {
  padding-top: 36px;
  transition: all 0.3s ease-in-out;

  @media (max-width: 600px) {
    position: relative;
    padding-top: 16px;
    transform: translateY(-240px);
    margin-top: -240px;
    // transform: translateY(0);
  }
}

.active {
  transform: translateY(0);
  margin-top: 0;
}
.item {
  font-weight: 300;
  font-size: 16px;
  line-height: 120%;
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

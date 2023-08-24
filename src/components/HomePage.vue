<template>
  <div class="all">
    
    <header class="header">
      <div class="xl:px-10 px-5 hidden justify-between w-full h-[80px] fixed top-0 left-0 z-10 bg-[#A07048]/80 xl:flex">
        <div class="flex items-center xl:gap-[20px] gap-[10px] ">
          <h1 class="text-[#fff] xl:text-[30px] text-[24px] ">TARIXMANBA.UZ</h1>
          <button class="btn flex justify-center items-center gap-2 bg-[#A20025] px-[16px] py-[14px]">
            <h4 class="text-[14px] text-white">MANBALAR</h4>
            <img class="w-[20px]" src="../assets/Group.png" alt="">
          </button>

          <!-- navbar -->
          <ul v-for="arr in NavbarArray" :key="arr" class="navbar flex   text-[#fff] ">
            <li class="">
              <router-link :to="arr.route">{{ arr.title }}</router-link>
            </li>
          </ul>
        </div>

        <ul class="flex items-center lg:gap-5 xxl:gap-[60px] gap-[5px] text-[16px]">
          <li class="">
            <div class="flex gap-2 items-center text-[#fff]">
              <img class="w-[16px] h-[16px]" src="../assets/person.png" alt="">
              <router-link to="#">Shaxsiy xona</router-link>
            </div>
          </li>
          <li>
            <div class="flex gap-2 items-center text-[#fff]">
              <img class="w-[18px] h-[18px]" src="../assets/ie.png" alt="">
              <router-link to="#">Zaif ko'ruvchilar uchun</router-link>
            </div>
          </li>
        </ul>
      </div>
    </header>

    <section class="hero">
      <div class="container">
        <div class="flex justify-center pt-24">
          <img src="../assets/icon.png" alt="">
        </div>
        <div class="flex justify-center  pt-[50px] text-[#fff]">
          <h1 class="text-[22px] text-center">Saytning toʻliq imkoniyatlaridan foydalanish uchun
            <span class="bord">Roʻyxatdan
              oʻting</span> yoki shaxsiy xonaga
            <span class="bord">kiring</span>
          </h1>
        </div>
        
        <!-- Search Input  -->
        <div class="flex justify-center pt-[50px] relative">
          <form>
            <label class="relative block">
              <input class=" xl:w-[500px] w-[300px] px-3 py-4 focus:outline-none" type="text" v-model="SearchInput"
                :placeholder="Search">
              <span class="absolute inset-y-0 right-0 flex items-center pr-3">
                <img class="" src="../assets/search.png" alt="">
              </span>
            </label>
          </form>
        </div>
        
        <!-- Barcha Manbalar Button -->
        <div class="flex justify-center mt-[40px]">
          <button class="btn px-[45px] py-[12px] bg-[#A20025] text-white text-[14px]">
            {{ btn }}
          </button>
        </div>
        
        <!-- Numbers -->
        <div class="flex justify-center flex-wrap row-auto gap-[40px] xl:gap-[120px] mt-[50px] xl:text-[25px] text-[22px] text-white ">
          <h1 class="text-center">
            {{ Text }}
            <div class="flex justify-center">
              <span class="number">15 000</span>
            </div>
          </h1>
          <h1 class="text-center">
            {{ Text1 }}
            <div class="flex justify-center">
              <span class="number">430</span>
            </div>
          </h1>
        </div>
      </div>
    </section>

    <!-- mobile -->
    <section class="mobile-header bg-white xl:hidden block fixed top-0 left-0 z-10 w-full">
      <!-- Burger -->
      <div class="mobile flex items-center justify-between px-4 py-3">
        <div class="burger-menu  xl:hidden block transition-all" @click="openMenu">
          <button v-if="!isMenuOpened"><img src="../assets/burger.png" alt=""></button>
          <button v-else><img class="w-[30px]" src="../assets/exit.png" alt=""></button>
        </div>
        <div class="history">
          <h1>TARIXMANBA<span class="text-[#A0664E]">.UZ</span></h1>
        </div>
        <div>
          <img src="../assets/korzinka.png" alt="">
        </div>
      </div>
    </section>

    <transition name="mobile-nav">
      <div v-if="isMenuOpened" class="mobile-menu fixed left-0 top-16 h-[100vh] z-20 bg-white">
        <div class="mob-link pt-5 px-5 gap-4 ">
          <div class="flex gap-3 items-center">
            <img src="../assets/book.png" alt="">
            <li class="">
              <router-link to="/">{{ book }}</router-link>
            </li>
          </div>
          <img src="../assets/line.png" alt="">
          <div class="flex gap-3 items-center">
            <img src="../assets/home.png" alt="">
            <li> <router-link to="/">{{ home }}</router-link></li>
          </div>
          <img src="../assets/line.png" alt="">

          <div class="flex gap-3 items-center">
            <img src="../assets/call.png" alt="">
            <li> <router-link to="/">{{ call }}</router-link>
            </li>
          </div>
          <img src="../assets/line.png" alt="">

          <div class="flex gap-3 items-center">
            <img src="../assets/pers2.png" alt="">
            <li>
              <router-link to="/">{{ Prof }}</router-link>
            </li>
          </div>
          <img src="../assets/line.png" alt="">

        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      is_navbar_active: false,
      isMenuOpened: false,
      scrollTop: 0,
      NavbarArray: [
        {
          title: 'Biz haqimizda',
          route: '/'
        },
        {
          title: 'Yangiliklar',
          route: '/'

        },
        {
          title: 'Kutubxona',
          route: '/'

        },
        {
          title: "Bog'lanish",
          route: '/'
        },
      ],
      Search: 'Qidirmoq',
      SearchInput: '',
      btn: 'BARCHA MANBALAR',
      Text: 'Oʻzbek davlatchiligiga oid manbalar soni',
      Text1: 'Tarixmanba.uz satdagi manbalar soni',
      book: 'Elektron kutubxona',
      home: 'Biz haqimizda',
      call: 'Kontraktlar',
      Prof: 'Profil'
    }
  },
  computed: {
    // checkRouteToChangeNavColor() {
    //   const routeName = this.$route.name
    //   if (routeName === 'home') return 'bg-transparent'
    //   return 'bg-white'
    // },
    // checkRouteToChangeLinkColor() {
    //   const routeName = this.$route.name
    //   if (routeName === 'home') return 'text-white'
    //   if (!routeName === 'home' || this.scrollTop > 0) return 'text-white'
    //   return 'text-black'
    // },
    // checkRouteToChangeBorder() {
    //   const routeName = this.$route.name
    //   if (routeName === 'home') return 'border-white/30'
    //   return 'border-black/30'
    // },
  },
  methods: {
    handleScroll() {
      this.scrollTop = window.scrollY
    },
    openMenu() {
      if (this.isMenuOpened == false) {
        this.isMenuOpened = true
      } else {
        this.isMenuOpened = false
      }
    },
    openDropdown(idx) {
      if (idx === 0) {
        this.menuArray[idx].isDropdownOpened = !this.menuArray[idx].isDropdownOpened;
      }
      if (idx === 3) {
        this.menuArray[idx].isDropdownOpened = !this.menuArray[idx].isDropdownOpened;
      }
    },
    isActive() {
      if (this.isDropdownActive == false) {
        this.isDropdownActive = true
      } else {
        this.isDropdownActive = false
      }
    },
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Proxima+Nova&display=swap');
@import "../assets/style.css";

.mobile-nav-enter-active,
.mobile-nav-leave-active {
  transition: 0.5s ease;
}

.mobile-nav-enter-from,
.mobile-nav-leave-to {
  transform: translate(-100%);
  opacity: 0;
}
</style>
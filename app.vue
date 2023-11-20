<script setup>
import gsap from 'gsap';
import {ScrollTrigger} from 'gsap/ScrollTrigger';
import avatar from '~/assets/img/avatar.svg'
import aspirasi from '~/assets/img/aspirasidesa.png'
import nizny from '~/assets/img/nizny.png'
import musicplayer from '~/assets/img/musicplayer.png'
import undangan from '~/assets/img/undangan.png'
import {register} from 'swiper/element/bundle';

register();

const menu = ref(false)

const dataProject = reactive([
  {
    image: aspirasi,
    title: 'CMS Aspirasi Desa',
    description: 'Proyek ini bertujuan untuk menciptakan sebuah platform online yang memberikan ruang bagi penduduk desa untuk berbagi ide, memberikan aspirasi, dan memperkuat komunikasi antara warga desa. Website ini memfasilitasi tiga jenis pengguna utama: admin, user, dan tamu, dengan tujuan meningkatkan partisipasi masyarakat dalam pembangunan desa.',
    github: 'https://github.com/cmsaspirasidesa/asp-desa-frontend'
  },
  {
    image: musicplayer,
    title: 'Music Player',
    description: 'Platform pengelolaan album dan musik online yang memungkinkan pengguna untuk menyusun dan mengelola koleksi musik mereka. Selain itu, platform ini menyediakan fitur pemutar musik terintegrasi sehingga pengguna dapat mendengarkan lagu-lagu favorit mereka secara online. Proyek ini masih dalam tahap pengembangan, dan beberapa fitur backend belum sepenuhnya diimplementasikan.',
    github: 'https://github.com/rhenoresky/Fe_MusicPlayer'
  },
  {
    image: undangan,
    title: 'Undangan Pernikahan',
    description: 'Undangan pernikahan secara online, memungkinkan pengantin untuk menghemat waktu dan biaya dalam penyebaran informasi. Website ini menyajikan informasi lengkap seputar acara pernikahan, dari detail pengantin, reservasi undangan, jadwal akad dan resepsi, lokasi, galeri foto, hingga ucapan selamat dari tamu. Fitur khusus seperti music pengiring dan hitung mundur tanggal pernikahan juga disediakan untuk meningkatkan pengalaman pengguna.',
    github: 'https://github.com/rhenoresky/undangan-anis'
  },
  {
    image: nizny,
    title: 'Landing Page Nizny',
    description: 'Sebuah website landing page yang dirancang untuk menyajikan informasi lengkap tentang layanan yang ditawarkan, paket harga, profil perusahaan, kontak yang dapat dihubungi, dan portofolio pekerjaan yang sudah diselesaikan. Website ini dibangun menggunakan HTML, CSS, dan JavaScript, dengan tambahan Bootstrap untuk tata letak responsif dan AOS (Animate On Scroll) untuk animasi elemen saat di-scroll.',
    github: 'https://github.com/rhenoresky/nizny'
  }
])
const spaceBetween = 12;

onMounted(() => {
  gsap.registerPlugin(ScrollTrigger);
  const tlAvatar = gsap.timeline({
    scrollTrigger: {
      trigger: '#avatarBox',
      start: '-100px center'
    },
  })

  const tlAbout = gsap.timeline({
    scrollTrigger: {
      trigger: '#avatarBox',
      start: '-100px center',
    },
  })

  gsap.to('#blobOne', {
    keyframes: [{x: '-40%', y: '40%', duration: 2}, {x: '-80%', y: '0%', duration: 2}, {x: '160%', y: '0%', duration: 6}, {x: '120%', y: '-40%', duration: 2}, {x: '80%', y: '0%', duration: 2},],
    repeat: -1,
    yoyo: true,
  })
  gsap.to('#blobTwo', {
    keyframes: [{x: '40%', y: '-40%', duration: 2}, {x: '80%', y: '0%', duration: 2}, {x: '-160%', y: '0%', duration: 6}, {x: '-120%', y: '40%', duration: 2}, {x: '-80%', y: '0%', duration: 2},],
    repeat: -1,
    yoyo: true,
  })
  gsap.to('#hello', {
    opacity: 1,
    duration: 5,
  })
  gsap.fromTo('#welcome', {
    x: -850,
  }, {
    x: 0,
    duration: 3,
    ease: 'power3.out',
    opacity: 1
  })

  tlAvatar.to("#avatarBox", {
    scale: 1,
    rotation: 360,
    duration: 2
  }).to("#avatar", {
    opacity: 1,
    duration: 2,
  })

  tlAbout.fromTo("#about", {
    x: 75,
    opacity: 0,
  }, {
    x: 0,
    opacity: 1,
    duration: 1,
    stagger: {
      amount: 0.5,
      ease: 0.5,
      from: 0,
    }
  }).from("#blobThree", {
    y: 550,
    ease: 'power3.out',
    duration: 2,
  })

  gsap.from('#portfolioHead', {
    scrollTrigger: {
      trigger: '#portfolioHead',
    },
    x: 100,
    opacity: 0,
    duration: 1.5,
  })

  gsap.from('#portfolioItem', {
    scrollTrigger: {
      trigger: '#portfolioItem',
    },
    y: 100,
    opacity: 0,
    duration: 1.5,
    stagger: {
      amount: 1.5,
      each: 0.5,
      from: 0,
    }
  })

  gsap.from('#contackItem', {
    scrollTrigger: {
      trigger: '#contackItem',
      start: '-60px center'
    },
    x: -100,
    opacity: 0,
    duration: 1.5,
    stagger: {
      amount: 1,
      each: 0.5,
      from: 0,
    }
  })
})
</script>

<template>
  <header
    class="hover:bg-[#fff] transition duration-500 ease-in-out hover:bg-opacity-5 h-20 top-0 w-full absolute z-50 flex justify-between items-center md:px-20 px-10 text-slate-100">
    <span
      class="font-great w-14 text-4xl hover:bg-gradient-to-r from-[#aeff4f] to-[#ff4545] bg-clip-text transition duration-500 ease-in-out hover:text-transparent">
      R
    </span>
    <nav class="relative">
      <button class="md:hidden" @click="menu = !menu">
        <Icon :name="menu ? 'radix-icons:cross-1' : 'radix-icons:hamburger-menu'" color="white" size="32px" />
      </button>
      <ul :class="menu ? 'flex' : 'hidden'"
        class="md:flex flex-col md:relative md:bg-transparent md:text-slate-100 absolute bg-slate-100 text-slate-900 px-8 rounded md:py-0 md:px-0 py-4 right-10 top-1 md:flex-row justify-center items-center md:gap-8 gap-4 uppercase font-montserrat text-sm font-semibold">
        <li
          class="hover:bg-gradient-to-r from-[#94B3FD] to-[#FF449F] bg-clip-text transition duration-500 ease-in-out hover:text-transparent hover:scale-110">
          <a href="#home">Home</a>
        </li>
        <li
          class="hover:bg-gradient-to-r from-[#aeff4f] to-[#ff4545] bg-clip-text transition duration-500 ease-in-out hover:text-transparent hover:scale-110">
          <a href="#avatarScreen">About</a>
        </li>
        <li
          class="hover:bg-gradient-to-r from-[#94B3FD] to-[#FF449F] bg-clip-text transition duration-500 ease-in-out hover:text-transparent hover:scale-110">
          <a href="#contack">Contack</a>
        </li>
      </ul>
    </nav>
  </header>
  <main id="home" class="md:px-4 w-full h-auto">
    <div class="w-full md:h-screen h-[320px] relative px-4 md:px-0">
      <div class="w-full md:h-screen h-full absolute flex justify-center items-center blur-3xl z-10 overflow-hidden">
        <section id="blobOne" class="md:w-[400px] md:h-[400px] w-[200px] h-[200px] backdrop-blur-3xl">
          <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
            <defs>
              <linearGradient id="fill" x1="0%" y1="0%" x2="100%" y2="0%" gradientTransform="rotate(91 0.5 0.5)">
                <stop offset="0%" stop-color="#aeff4f"></stop>
                <stop offset="100%" stop-color="#ff4545"></stop>
              </linearGradient>
            </defs>
            <path fill="url(#fill)">
              <animate attributeName="d" dur="5000ms" repeatCount="indefinite" values="M78,73Q65,96,39,86.5Q13,77,16,52.5Q19,28,42,16.5Q65,5,78,27.5Q91,50,78,73Z;
          M79.5,71.5Q64,93,40.5,83.5Q17,74,14.5,48.5Q12,23,38.5,14Q65,5,80,27.5Q95,50,79.5,71.5Z;
          M78.5,67Q61,84,36.5,81Q12,78,16,53Q20,28,42,18Q64,8,80,29Q96,50,78.5,67Z;
          M73,66.5Q61,83,39.5,78Q18,73,19.5,51Q21,29,42.5,18Q64,7,74.5,28.5Q85,50,73,66.5Z;
          M78,73Q65,96,39,86.5Q13,77,16,52.5Q19,28,42,16.5Q65,5,78,27.5Q91,50,78,73Z;">
              </animate>
            </path>
          </svg>
        </section>
        <section id="blobTwo" class="md:w-[400px] md:h-[400px] w-[200px] h-[200px] backdrop-blur-3xl">
          <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
            <defs>
              <linearGradient id="gradient" x1="0%" y1="0%" x2="100%" y2="0%" gradientTransform="rotate(91 0.5 0.5)">
                <stop offset="0%" stop-color="#FF449F"></stop>
                <stop offset="100%" stop-color="#94B3FD"></stop>
              </linearGradient>
            </defs>
            <path fill="url(#gradient)">
              <animate attributeName="d" dur="5000ms" repeatCount="indefinite" values="M78,73Q65,96,39,86.5Q13,77,16,52.5Q19,28,42,16.5Q65,5,78,27.5Q91,50,78,73Z;
          M79.5,71.5Q64,93,40.5,83.5Q17,74,14.5,48.5Q12,23,38.5,14Q65,5,80,27.5Q95,50,79.5,71.5Z;
          M78.5,67Q61,84,36.5,81Q12,78,16,53Q20,28,42,18Q64,8,80,29Q96,50,78.5,67Z;
          M73,66.5Q61,83,39.5,78Q18,73,19.5,51Q21,29,42.5,18Q64,7,74.5,28.5Q85,50,73,66.5Z;
          M78,73Q65,96,39,86.5Q13,77,16,52.5Q19,28,42,16.5Q65,5,78,27.5Q91,50,78,73Z;">
              </animate>
            </path>
          </svg>
        </section>
      </div>
      <article class="flex justify-center font-bold flex-col w-full md:gap-8 gap-6 md:h-screen font-montserrat">
        <h1 id="hello"
          class="uppercase md:text-9xl text-4xl text-end md:mt-10 mt-24 text-slate-100 tracking-wider opacity-0">
          Hello, I'm<br>Rheno Resky<br>Nugraha
        </h1>
        <p id="welcome" class="uppercase md:text-5xl text-2xl text-start text-slate-100 tracking-wider opacity-0">Welcome
          to my
          portfolio</p>
      </article>
    </div>
    <div id="avatarScreen"
      class="md:h-screen h-[680px] md:pl-16 w-full flex flex-col md:flex-row md:pt-0 pt-4 mt-10 md:mt-0 items-center md:gap-4 md:justify-center">
      <section class="md:basis-4/12 md:px-0 px-4 md:w-full w-2/3 md:h-full flex justify-center items-center">
        <div id="avatarBox" class="ring-2 scale-0 ring-slate-100 rounded">
          <img id="avatar" class="opacity-0" :src=avatar alt="avatar">
        </div>
      </section>
      <section class="md:basis-6/12 w-full h-full flex flex-col relative overflow-hidden md:pt-0 pt-10">
        <div id="blobThree" class="w-full absolute md:top-8 top-0 md:right-6 z-10 blur-2xl">
          <svg viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
            <path fill="#00fbff44"
              d="M38.8,-50.1C54.2,-42.1,73.5,-36.1,79.3,-24.4C85.1,-12.6,77.3,5,67.7,18.1C58.1,31.3,46.7,40,35.1,45.7C23.6,51.4,11.8,54.1,0.2,53.8C-11.3,53.5,-22.7,50.1,-29.3,42.8C-35.9,35.5,-37.8,24.2,-42.1,13.1C-46.4,2.1,-53.2,-8.7,-56.1,-23.9C-59,-39.2,-58.1,-58.9,-48.1,-68.7C-38.1,-78.5,-19,-78.3,-3.7,-73.2C11.6,-68.1,23.3,-58.1,38.8,-50.1Z"
              transform="translate(100 100)" />
          </svg>
        </div>
        <div class="w-full md:px-0 px-4 h-full flex flex-col md:justify-center md:items-center absolute z-20">
          <h2 id="about"
            class="uppercase md:text-6xl text-3xl font-semibold font-montserrat text-center text-slate-100 mb-4 md:mb-10">
            About me
          </h2>
          <p id="about" class="md:text-2xl text-lg font-light text-center text-slate-100 md:w-2/3">
            I am an individual who enjoys learning about the world of technology. My enthusiasm for learning drives me to
            continually expand my knowledge and skills. My desire to explore new things enables me to stay relevant in the
            rapidly evolving world of technology
          </p>
        </div>
      </section>
    </div>
    <div class="w-full md:h-[620px] md:px-0 px-4 h-[600px] md:pt-14 overflow-hidden">
      <h2 id="portfolioHead"
        class="uppercase md:text-6xl text-3xl font-semibold font-montserrat text-center text-slate-100 mb-10">
        Portfolio
      </h2>
      <swiper-container slides-per-view="1" :space-between="spaceBetween" :pagination="{ hideOnClick: true }"
        :breakpoints="{ 768: { slidesPerView: 3, } }">
        <swiper-slide id="portfolioItem" v-for="(project, i) of dataProject" :key="i" class="bg-[#252438] p-6 rounded">
          <div class="overflow-hidden rounded-md mb-4">
            <img :src="project.image" alt="AspirasiDesa">
          </div>
          <div class="text-slate-100">
            <h3 class="text-2xl font-montserrat font-semibold mb-1">
              {{ project.title }}
            </h3>
            <p class="text-lg font-light mb-2 line-clamp-3">
              {{ project.description }}
            </p>
            <div class="flex gap-2 mb-8">
              <a href="project.github"
                class="text-lg font-light hover:bg-gradient-to-r from-[#aeff4f] to-[#ff4545] bg-clip-text transition duration-500 ease-in-out hover:text-transparent">Lihat
                selengkapnya</a>
              <a :href="project.github" class="w-8 h-8">
                <Icon name="uil:github" color="white" size="32px" />
              </a>
            </div>
          </div>
        </swiper-slide>
      </swiper-container>
    </div>
  </main>
  <footer id="contack" class="w-full md:px-0 h-auto md:mt-24 text-slate-100 flex-wrap px-4">
    <div class="w-full flex md:flex-row flex-col md:gap-0 gap-8 mb-10">
      <section id="contackItem" class="md:basis-1/3 w-full h-full flex flex-col items-center gap-4">
        <h3 class="text-xl font-semibold font-montserrat">Contack</h3>
        <ul class="flex flex-col gap-3 items-center">
          <li>
            <Icon name="logos:whatsapp-icon" size="24px" /><a href="https://wa.me/081214196304"
              class="ml-2">081214196304</a>
          </li>
          <li>
            <Icon name="logos:google-gmail" size="24px" /><a href="mailto:rheno2002@gmail.com"
              class="ml-2">rheno2002@gmail.com</a>
          </li>
        </ul>
      </section>
      <section id="contackItem" class="md:basis-1/3 w-full h-full flex flex-col items-center gap-4">
        <h3 class="text-xl font-semibold font-montserrat text-center">Technology Used</h3>
        <ul class="flex flex-col gap-3 items-center">
          <li>
            <Icon name="logos:nuxt-icon" size="24px" /><span class="ml-2">Nuxt 3</span>
          </li>
          <li>
            <Icon name="devicon:tailwindcss" size="24px" /><span class="ml-2">Tailwind</span>
          </li>
          <li>
            <Icon name="logos:greensock-icon" size="24px" /><span class="ml-2">GSAP</span>
          </li>
          <li class="flex">
            <svg width="24" height="24" viewBox="0 0 129 129" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M97.5869496,9.51093626 C115.83804,20.7848256 128,40.9721238 128,64 C128,99.346224 99.346224,128 64,128 C56.2920179,128 48.9022945,126.637372 42.0606106,124.137797 L41.3296807,123.865645 L42.5199148,123.48344 L44.0499006,122.981598 L44.8047554,122.729449 L44.8047554,122.729449 L45.5528525,122.476476 L47.0287766,121.968044 L48.477679,121.456268 L49.8995657,120.941118 L51.2944429,120.422561 L51.9817549,120.161995 L53.3361292,119.638268 C54.7663971,119.077773 56.1505947,118.511327 57.4887554,117.938757 L58.4837445,117.508179 L59.7032082,116.966702 C60.2391997,116.725238 60.7672019,116.482694 61.2872173,116.239057 L62.0612505,115.87278 L63.1998411,115.320271 L63.7590314,115.042615 L63.7590314,115.042615 L64.3114862,114.76402 L65.3961918,114.203997 C74.5017145,109.427674 80.6883363,104.239002 83.9729034,98.5499653 C90.9321253,86.4962393 84.8542511,73.6150855 67.4065187,60.4830885 L65.9866432,59.4185495 L65.1241488,58.7570907 L64.2867532,58.1006716 L63.4743719,57.4492672 L62.6869203,56.8028527 L62.3025167,56.4815088 L62.3025167,56.4815088 L61.9243138,56.161403 L61.1864678,55.5248932 L60.6492814,55.0507377 L60.6492814,55.0507377 L60.1259396,54.5793364 L59.4496246,53.9550673 L58.7977741,53.3356509 L58.1703034,52.7210621 L57.865684,52.4155703 L57.865684,52.4155703 L57.5671278,52.1112761 L56.9881629,51.5062679 C50.0910281,44.1742986 48.550875,37.8976624 51.6821025,32.4742173 C53.275799,29.713854 56.0387768,26.999998 59.9662039,24.3569485 L60.4430842,24.040124 L61.1940488,23.5569049 C61.5336196,23.3425039 61.8809347,23.1285905 62.2359916,22.9151777 L62.7743828,22.5954356 L63.603739,22.1172522 L64.4592124,21.6408141 L65.1179529,21.2846511 L65.1179529,21.2846511 L65.7913778,20.9295026 L66.7121153,20.4575739 C67.4124544,20.1043216 68.1348104,19.7526404 68.8791706,19.4025938 L69.6308651,19.0530944 L70.6559388,18.5888147 L71.1782513,18.3574212 L72.2424237,17.8961475 L72.7842819,17.6662758 L73.887538,17.2080833 L74.4489343,16.9797709 L75.5912592,16.5247346 L76.1721862,16.2980192 L77.353565,15.8462143 L78.5609715,15.3966054 L79.174433,15.1726349 L80.4208685,14.7263826 L81.6933149,14.2824097 L82.9917658,13.8407497 L83.6507409,13.6207974 L84.9881859,13.1826691 L86.3516187,12.7469371 L87.7410327,12.3136347 L89.1564212,11.8827954 L90.5977776,11.4544525 L92.4359804,10.9225852 L94.3147346,10.394736 L96.6227494,9.76671243 L97.5869496,9.51093626 Z M64,0 C71.7830114,0 79.2415381,1.38928435 86.1411179,3.93339103 L86.8782091,4.21038217 L86.4108627,4.35186467 L84.1313124,5.0545346 L83.3848908,5.2905768 L81.9121853,5.76541455 L80.4663248,6.24395126 L79.0473024,6.72622031 L77.6551115,7.21225509 L76.2897456,7.70208898 L75.6171199,7.94844102 L73.9648828,8.56854028 L72.3545311,9.19471909 L71.0963985,9.70008321 L70.4773795,9.95425044 L69.2594321,10.4655761 C56.8123589,15.7699668 48.6548341,21.7176 44.7538993,28.4742173 C37.9453585,40.2669559 44.1208291,52.9796592 61.5702618,66.1081375 L62.9900625,67.1727537 L63.8522936,67.8346365 L64.6892575,68.491774 L65.09829,68.8185721 L65.8975078,69.468645 L66.4804703,69.9531308 L66.4804703,69.9531308 L67.0493707,70.4349994 L67.7860906,71.0734406 L68.1451248,71.3909334 L68.8445933,72.0224812 C69.2263095,72.3720718 69.5965761,72.7195512 69.9554568,73.0649416 L70.4852463,73.5814631 L71.248012,74.3504059 L71.9726186,75.1123909 C78.8402712,82.495364 80.3081527,88.8974997 77.0447002,94.5499653 C74.933031,98.2074836 70.9013706,101.807999 64.958951,105.303275 L64.4134675,105.620736 L63.5293583,106.121564 L62.6189315,106.620891 C62.1058295,106.897871 61.5805462,107.174142 61.0430864,107.449677 L60.227765,107.862426 L59.2252746,108.356245 L58.1964941,108.848418 L57.1414295,109.338914 L56.6040425,109.583523 L55.5095633,110.071443 L54.3888152,110.557607 L53.2418044,111.041982 L52.6584524,111.283488 L51.4720589,111.76512 L50.869019,112.005238 L50.869019,112.005238 L50.259418,112.244884 L49.0205357,112.722748 L47.755418,113.19868 L46.4640712,113.672647 L45.1465013,114.144619 L43.8027143,114.614564 L43.1209914,114.848766 L41.7378904,115.315609 L41.0365138,115.548243 L39.6141124,116.011914 L38.1655184,116.47343 L36.3179518,117.047246 L34.4294807,117.617582 L32.8892605,118.071305 L30.739698,118.689489 C12.3072163,107.455464 0,87.1649844 0,64 C0,28.653776 28.653776,0 64,0 Z"
                transform="translate(.335 .835)" fill="#0080FF" />
            </svg>
            <span class="ml-2">Swiper</span>
          </li>
        </ul>
      </section>
      <section id="contackItem" class="md:basis-1/3 w-full h-full flex flex-col items-center gap-4">
        <h3 class="text-xl font-semibold font-montserrat text-center">Social Media</h3>
        <ul class="flex flex-col gap-3 items-center">
          <li>
            <Icon name="uil:github" color="white" size="32px" /><a href="https://github.com/rhenoresky"
              class="ml-2">rhenoresky</a>
          </li>
          <li>
            <Icon name="logos:linkedin-icon" size="24px" /><a href="https://www.linkedin.com/in/rheno-resky-nugraha/"
              class="ml-2">Rheno Resky Nugraha</a>
          </li>
        </ul>
      </section>
    </div>
    <hr>
    <div class="py-4 text-lg font-light flex justify-center">
      &copy; 2023 &bull; Rheno Resky Nugraha
    </div>
  </footer>
</template>

<style>
* {
  --swiper-pagination-bottom: 12px;
  --swiper-pagination-bullet-size: 12px;
  --swiper-pagination-bullet-width: 12px;
  --swiper-pagination-bullet-height: 12px;
}

html {
  scroll-behavior: smooth;
}

body {
  background-color: #191825;
  width: 100%;
}
</style>
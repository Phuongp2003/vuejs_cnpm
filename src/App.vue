<script setup>
import { ref } from 'vue'
import Navbar from './components/Navbar.vue'
import Slide from './components/Slide.vue'
import Cards from './components/Cards.vue'
import Footer from './components/Footer.vue'
import Return from './components/Return.vue'
import ProjectInfo from './components/ProjectInfo.vue';
import ProjectCommit from './components/ProjectCommit.vue'

const db = ref({
  cards: [{
    name: 'Game',
    tool: 'Godot',
    image: '/public/images/Godot-bg.png',
    icon: '/public/images/icon.svg',
    id: 1
  },
  {
    name: 'Web',
    tool: 'Java Spring MVC',
    image: 'unsplash-photo-2.jpg',
    icon: '/public/images/spring-icon-svgrepo-com.svg',
    id: 2
  },
  {
    name: 'Desktop app',
    tool: 'C++',
    image: '/public/images/desktop-app.png',
    icon: '/public/images/cplusplus-svgrepo-com.svg',
    id: 3
  }]
}
)
</script>

<template>
  <Navbar />

  <div class="main-container" v-if="receivedData === 0">
    <Slide />
    <Cards :cards="db.cards" title="Danh mục sản phẩm" @cpage="handleChildData">
    </Cards>
  </div>

  <div class="main-container" v-if="receivedData === 1">
    <ProjectInfo projectName="phuongp2003/MyGodotProject" />
    <ProjectCommit projectName="phuongp2003/MyGodotProject" />
  </div>

  <div class="main-container" v-if="receivedData === 2">
    <ProjectInfo projectName="phuongp2003/LTWeb_PTITHCM" />
    <ProjectCommit projectName="phuongp2003/LTWeb_PTITHCM" />
  </div>

  <div class="main-container" v-if="receivedData === 3">
    <ProjectInfo projectName="phuongp2003/CTDL_N7" />
    <ProjectCommit projectName="phuongp2003/CTDL_N7" />
  </div>

  <div class="return-to-home" v-if="receivedData !== 0">
    <Return @click="receivedData = 0" />
  </div>
  <Footer />
</template>

<style scoped>
.return-to-home {
  position: fixed;
  top: 80px;
  right: 120px;
}
</style>

<script>
import ChildComponent from './components/Cards.vue';

export default {
  components: {
    ChildComponent,
  },
  data() {
    return {
      receivedData: 0
    };
  },
  methods: {
    handleChildData(data) {
      this.receivedData = data;
    },
  },
};

</script>

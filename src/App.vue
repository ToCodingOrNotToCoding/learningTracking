<template>
  <div class="container">
    <div class="navbar">
      <!-- 导航栏选项 -->
      <div class="nav-item" @click="scrollToSection(1)">学习活动可视化</div>
      <div class="nav-item" @click="scrollToSection(2)">Section 2</div>
      <div class="nav-item" @click="scrollToSection(3)">Section 3</div>
    </div>
    <div class="content">
      <!-- 内容区的各个部分 -->
      <div id="section1">
        <div>
          <h2>学习活动可视化</h2>
        </div>
        <p>
          <learningActivateChart></learningActivateChart>
        </p>
      </div>
      <div id="section2">
        <h2>Section 2</h2>
        <courseProgress></courseProgress>
      </div>
      <div id="section3">
        <h2>Section 3</h2>
        <p>内容区的第三部分</p>
        <acknow></acknow>
      </div>

      <div id="section4">
        <h2>Section 4</h2>
        <p>内容区的第三部分</p>
        <habit></habit>
      </div>
    </div>
  </div>
</template>

<script>
import learningActivateChart from "./components/learningActivateChart.vue"
import courseProgress from "./components/courseProgress.vue"
import acknow from "./components/acknow.vue"
import habit from "./components/learnHabit.vue"
export default {
  methods: {
    scrollToSection(index) {
      const sectionId = 'section' + index;
      const sectionElement = document.getElementById(sectionId);
      if (sectionElement) {
        sectionElement.scrollIntoView({ behavior: 'smooth' });
      }
    }
  },
  components: {
    learningActivateChart, courseProgress, acknow,habit
  }
};
</script>

<style scoped>
.container {
  display: flex;
}

.navbar {
  flex-basis: 25%;
}

.content {
  flex-basis: 75%;
  overflow-y: scroll;
  height: 90vh;

}


.nav-item {
  cursor: pointer;
}
</style>
